# Python Quick-Ref

## Managing python versions, environments and dependencies

**Use uv!**

### "uv-first" projects


* Initialize new project

  ```sh
  uv init {project_name}
  ```

* Initialize existing project and install deps

  ```sh
  uv sync
  ```

* Install and update existing deps

  ```sh
  uv sync --upgrade
  ```

* Add dep

  ```sh
  uv add {dep}[version_constraint]
  ```

* Remove dep

  ```sh
  uv remove {dep}
  ```

* Upgrade dep

  ```sh
  uv lock --upgrade-package {dep}
  ```

### uv-first scripts

```sh
uv add --script example.py pandas  # Legger til kommentar på toppen av filen
uv run example.py
```

## Debugging and troubleshooting

* Debugging pandas dataframes and series, plot pd.Series:

  ```python
  breakpoint()  # Stop execution and enter debugger. Enter the remaining into debug console at the right time
  import matplotlib.pyplot as plt
  df.plot()
  plt.show()  # plot appears
  ```

## Convenient cli's

* Generate a uuid: `python -m uuid`

* Serve static files in current directory: `python -m http.server 8000`

## Logging in pytest output

```bash
pytest -o log_cli=true --log-level=DEBUG
```

or persistant in a config file, which by convention resides in the root directory of the repository

```ini
# pytest.ini
log_cli=true
log_level=DEBUG
```

```toml
# pyproject.toml
[tool.pytest.ini_options]
log_cli="true"
log_level="DEBUG"
```

[ref pytest docs](https://docs.pytest.org/en/7.1.x/reference/customize.html?highlight=configuration)

## Ruff

* Format: `ruff format {file|dir}`

* Lint: `ruff check [--fix] {file|dir}`

* Organize imports: `ruff check --fix --select I`
  or add to pyproject.toml:

  ```toml
  [tool.ruff.lint]
  extend-select = ["I"]
  ```

* Example config:

  ```toml
  [tool.ruff]
  line-length = 120

  [tool.ruff.lint]
  extend-select = ["I"]

  [tool.ruff.lint.isort]
  known-first-party = ["myorg_*"]
  ```

## BasedPyright

A fork of the Pyright LSP with various feature improvements, such as code action for
missing imports!

Works nicely with terminal editors like Helix.

See https://docs.basedpyright.com/latest/

## Interesting Python / JS Interop project

[PythonMonkey](https://github.com/Distributive-Network/PythonMonkey)
[Kode24 Article](https://www.kode24.no/artikkel/bygger-bro-mellom-javascript-og-python-med-pythonmonkey/81670827)

