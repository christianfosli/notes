# Python Quick-Ref

## Managing multiple python versions and dependencies

* Install multiple python versions with dnf:
  [developer.fedoraproject.org/tech/languages/python/multiple-pythons](https://developer.fedoraproject.org/tech/languages/python/multiple-pythons.html)

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


## Convenient cli's

* Generate a uuid: `python -m uuid`
