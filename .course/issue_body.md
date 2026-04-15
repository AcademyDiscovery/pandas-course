## Summary

`tests/computation/test_eval.py::TestOperations::test_assignment_not_inplace` is marked `xfail` with reason `"Unknown: Omitted test_ in name prior."` The test was previously named without a `test_` prefix so pytest never collected it. When it was renamed, it started failing — but the failure is due to a bug **in the test itself**, not in pandas.

## The bug

The test checks that `df.eval("c = a + b", inplace=False)` does **not** modify `df` in place. However, the final assertion compares `df` (2 columns) against `expected` (3 columns, including `"c"`):

```python
actual = df.eval("c = a + b", inplace=False)
expected = df.copy()
expected["c"] = expected["a"] + expected["b"]
tm.assert_frame_equal(df, expected)  # wrong: compares `df` instead of `actual`
```

This assertion would only pass if `df` *was* modified in place — the exact bug the test was meant to guard against (GH#9297).

## Fix

- Remove the `xfail` marker
- Replace `tm.assert_frame_equal(df, expected)` with `tm.assert_frame_equal(actual, expected)`
- Add a check that `df` is unchanged, e.g. `assert list(df.columns) == ["a", "b"]`