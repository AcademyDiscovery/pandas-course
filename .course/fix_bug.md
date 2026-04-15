# Fix Bug

## Step: Understand the issue

> Read the issue and linked test file. Find what assertion is wrong and why it causes an incorrect xfail.

## Step: Explore the codebase

> Search for `test_assignment_not_inplace` in pandas/tests and open the relevant file.

## Step: Reproduce the problem

> Run the test with `pytest -xvs path/to/test.py::test_name` and confirm the failure.

## Step: Plan your change

> Identify the minimal fix. Prefer correcting the assertion logic over suppressing the xfail marker.

## Step: Implement & test

> Make your change, re-run the test, then run the full suite. Comment on the issue when ready.

## Footer

- [Contribution guide ↗](https://pandas.pydata.org/docs/dev/development/contributing.html)
- [Code style ↗](https://pandas.pydata.org/docs/dev/development/contributing_codebase.html)
- [Test docs ↗](https://pandas.pydata.org/docs/dev/development/contributing_documentation.html)
