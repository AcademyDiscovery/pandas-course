# Environment Setup

## Step: Install C compiler

### collapsible: macOS [default-on-mac]

```
xcode-select --install
```

### collapsible: Windows [default-on-windows]

> Install Build Tools for Visual Studio
> (visualstudio.microsoft.com/downloads)

### collapsible: Linux [default-on-linux]

```
gcc --version
```

## Step: Create virtual environment

> Option A — conda:

```
conda env create --file environment.yml
conda activate pandas-dev
```

> Option B — pip:

> macOS / Linux:

```
python3 -m venv ~/virtualenvs/pandas-dev
source ~/virtualenvs/pandas-dev/bin/activate
```

> Windows:

```
python -m venv %USERPROFILE%\virtualenvs\pandas-dev
%USERPROFILE%\virtualenvs\pandas-dev\Scripts\activate
```

## Step: Build & install in editable mode

```
python -m pip install --editable . --no-build-isolation
```

> Editable install — takes ~2 min

## Step: Run test suite to verify

```
python -m pytest pandas/tests/ -x -q
```

## Footer

- [Full setup guide ↗](https://pandas.pydata.org/docs/dev/development/contributing_environment.html)
- [Troubleshooting ↗](https://pandas.pydata.org/docs/dev/development/contributing.html)
- [Conda docs ↗](https://conda.io/projects/conda/en/latest/user-guide/index.html)
