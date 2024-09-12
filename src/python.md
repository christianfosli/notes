# Python Quick-Ref

## Managing multiple python versions and dependencies

**TODO**

Consider managing python environments with [**uv**](https://github.com/astral-sh/uv) instead.
It supports managing venv's, global python installations, tools (similar to pipx), etc

---

* Install multiple python versions with system package manager (e.g. dnf:
  [developer.fedoraproject.org/tech/languages/python/multiple-pythons](https://developer.fedoraproject.org/tech/languages/python/multiple-pythons.html))

* Use venv to separate project dependencies from system python dependencies:

  ```sh
  python -m venv venv
  . ./venv/bin/activate
  # pip install away
  ```

  Or with an older version of python:

  ```sh
  python3.11 -m venv venv
  . ./venv/bin/activate
  # pip install away
  ```

* [More info about venv's](https://realpython.com/python-virtual-environments-a-primer/)

## Pip upgrades

1. Update version constraints in requirements.txt

2.

  ```sh
  pip install --upgrade -r requirements.txt
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

## Interesting Python / JS Interop project

[PythonMonkey](https://github.com/Distributive-Network/PythonMonkey)
[Kode24 Article](https://www.kode24.no/artikkel/bygger-bro-mellom-javascript-og-python-med-pythonmonkey/81670827)

