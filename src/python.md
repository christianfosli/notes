# Python Quick-Ref

## Managing multiple python versions and dependencies

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
