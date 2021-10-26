# {{ cookiecutter.project_name }}
{{ cookiecutter.project_description }}

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![Pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/{{ cookiecutter.github_name }}/{{ cookiecutter.project_description }}/blob/master/.pre-commit-config.yaml)
[![Semantic Versions](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--versions-e10079.svg)](https://github.com/{{ cookiecutter.github_name }}/{{ cookiecutter.project_description }}/releases)
[![License](https://img.shields.io/github/license/tjmillsco/python-package-template)](https://github.com/{{ cookiecutter.github_name }}/{{ cookiecutter.project_description }}/blob/master/LICENSE)


## Very first steps

### Initialize your code

1. Initialize `git` inside your repo:

```bash
cd {{ cookiecutter.project_name }} && git init
```

2. If you don't have `Poetry` installed run:

```bash
make poetry-download
```

3. Initialize poetry and install `pre-commit` hooks:

```bash
make install
make pre-commit-install
```

4. Run the codestyle:

```bash
make codestyle
```

5. Upload initial code to GitHub:

```bash
git add .
git commit -m ":tada: Initial commit"
git branch -M main
git remote add origin https://github.com/{{ cookiecutter.github_name }}/{{ cookiecutter.project_name }}.git
git push -u origin main
```

### Poetry

Want to know more about Poetry? Check [its documentation](https://python-poetry.org/docs/).

Poetry's [commands](https://python-poetry.org/docs/cli/#commands) are very intuitive and easy to learn, like:

- `poetry add numpy@latest`
- `poetry run pytest`
- `poetry publish --build`

etc

## Features

In this project we bring best development practices for Python to Data Science.

### Development features

- Supports `Python 3.7` and higher.
- [`Poetry`](https://python-poetry.org/) as a dependencies manager. See configuration in [`pyproject.toml`](https://github.com/tjmillsco/python-ds-cookiecutter/blob/master/%7B%7B%20cookiecutter.project_name%20%7D%7D/pyproject.toml) and [`setup.cfg`](https://github.com/TezRomacH/python-package-template/blob/master/%7B%7B%20cookiecutter.project_name%20%7D%7D/setup.cfg).
- Automatic codestyle with [`black`](https://github.com/psf/black), [`isort`](https://github.com/timothycrosley/isort) and [`pyupgrade`](https://github.com/asottile/pyupgrade).
- Ready-to-use [`pre-commit`](https://pre-commit.com/) hooks with code-formatting.
- Type checks with [`mypy`](https://mypy.readthedocs.io); docstring checks with [`darglint`](https://github.com/terrencepreilly/darglint); security checks with [`safety`](https://github.com/pyupio/safety)
- Testing with [`pytest`](https://docs.pytest.org/en/latest/).

### Deployment features

- Everything is already set up for security checks, codestyle checks, code formatting, testing, linting, docker builds, etc with [`Makefile`](https://github.com/tjmillsco/python-ds-cookiecutter/blob/master/%7B%7B%20cookiecutter.project_name%20%7D%7D/Makefile#L89).
- [Dockerfile](https://github.com/tjmillsco/python-ds-cookiecutter/blob/master/%7B%7B%20cookiecutter.project_name%20%7D%7D/docker/Dockerfile) for your package.

## Installation

```bash
pip install -U {{ cookiecutter.project_name }}
```

or install with `Poetry`

```bash
poetry add {{ cookiecutter.project_name }}
```

{% if cookiecutter.create_example_template == 'cli' -%}Then you can run

```bash
{{ cookiecutter.project_name }} --help
```

or with `Poetry`:

```bash
poetry run {{ cookiecutter.project_name }} --help
```

[`Makefile`](https://github.com/{{ cookiecutter.github_name }}/{{ cookiecutter.project_name }}/blob/master/Makefile) contains a lot of functions for faster development.

## Development features

### To download and install Poetry run:

```bash
make poetry-download
```

To uninstall

```bash
make poetry-remove
```

### Install all dependencies and pre-commit hooks

Install requirements:

```bash
make install
```

Pre-commit hooks coulb be installed after `git init` via

```bash
make pre-commit-install
```

### Codestyle</summary>

Automatic formatting uses `pyupgrade`, `isort` and `black`.

```bash
make codestyle

# or use synonym
make formatting
```

Codestyle checks only, without rewriting files:

```bash
make check-codestyle
```

> Note: `check-codestyle` uses `isort`, `black` and `darglint` library

### Code security

```bash
make check-safety
```

This command launches `Poetry` integrity checks as well as identifies security issues with `Safety` and `Bandit`.

```bash
make check-safety
```

### Type checks</summary>

Run `mypy` static type checker

```bash
make mypy
```

### Tests

Run `pytest`

```bash
make test
```

### All linters

Of course there is a command to run all linters in one:

```bash
make lint
```

the same as:

```bash
make test && make check-codestyle && make mypy && make check-safety
```

### Docker

```bash
make docker-build
```

which is equivalent to:

```bash
make docker-build VERSION=latest
```

Remove docker image with

```bash
make docker-remove
```

More information [about docker](https://github.com/{{ cookiecutter.github_name }}/{{ cookiecutter.project_name }}/tree/master/docker).

### Cleanup
Delete pycache files

```bash
make pycache-remove
```

Remove package build

```bash
make build-remove
```

Or to remove pycache, build and docker image run:

```bash
make clean-all
```

## 📈 Releases

You can see the list of available releases on the [GitHub Releases](https://github.com/{{ cookiecutter.github_name }}/{{ cookiecutter.project_name }}/releases) page.

We follow [Semantic Versions](https://semver.org/) specification.

## 🛡 License

[![License](https://img.shields.io/github/license/{{ cookiecutter.github_name }}/{{ cookiecutter.project_name }})](https://github.com/{{ cookiecutter.github_name }}/{{ cookiecutter.project_name }}/blob/master/LICENSE)

## Credits 
This project was generated with [`python-package-template`](https://github.com/TezRomacH/python-package-template)
