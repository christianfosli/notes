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

### "pip-first" projects

* Initialize venv

  ```sh
  uv venv --python 3.12
  . .venv/bin/activate
  ```

  * If relying on internal packages using Azure DevOps Artifacts,
    the UV_EXTRA_INDEX_URL env variable can be used to configure this.
    A personal access token can be included in the URL for basic auth
    (see uv docs for details).

    For my current (2024) project I'm adjusting the venv activate script
    to set this environment variable when activating venv,
    and unset it in the deactivate function.
    It is also possible to add the index url to pyproject.toml,
    but then authorization must be handled differently, e.g. with artifacts-keyring
    (obviously don't check your PAT into git).

* Add dep

  ```sh
  uv pip install {dep}
  ```

  Or add it to requirements.txt and
  
  ```sh
  uv pip install -r requirements.txt
  ```

  Or add it to pyproject.toml dependencies and

  ```sh
  uv pip install -e .
  ```

* Remove dep

  ```sh
  uv pip uninstall {dep}
  ```

* Upgrade dep

  ```sh
  uv pip install -U {dep}
  ```

  Or update version constraints in requirements.txt if needed and

  ```sh
  uv pip install -U -r requirements.txt
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

