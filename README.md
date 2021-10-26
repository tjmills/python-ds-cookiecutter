# Python Data Science Project Generator

<div align="center">

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)
[![Pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit&logoColor=white)](https://github.com/tjmillsco/python-ds-cookiecutter/blob/master/.pre-commit-config.yaml)
[![Semantic Versions](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--versions-e10079.svg)](https://github.com/tjmillsco/python-ds-cookiecutter/releases)
[![License](https://img.shields.io/github/license/tjmillsco/python-package-template)](https://github.com/tjmillsco/python-package-template/blob/master/LICENSE)

</div>

## TL;DR

```bash
cookiecutter gh:tjmillsco/python-ds-cookiecutter
```

> All you need is the latest version of cookiecutter

## Features

In this [cookiecutter](https://github.com/cookiecutter/cookiecutter) template we bring best development practices for Python to Data Science.

### Development features

- Supports `Python 3.7` and higher.
- [`Poetry`](https://python-poetry.org/) as a dependencies manager. See configuration in [`pyproject.toml`](https://github.com/tjmillsco/python-ds-cookiecutter/blob/master/%7B%7B%20cookiecutter.project_name%20%7D%7D/pyproject.toml) and [`setup.cfg`](https://github.com/TezRomacH/python-package-template/blob/master/%7B%7B%20cookiecutter.project_name%20%7D%7D/setup.cfg).
- Automatic codestyle with [`black`](https://github.com/psf/black), [`isort`](https://github.com/timothycrosley/isort) and [`pyupgrade`](https://github.com/asottile/pyupgrade).
- Ready-to-use [`pre-commit`](https://pre-commit.com/) hooks with code-formatting.
- Type checks with [`mypy`](https://mypy.readthedocs.io); docstring checks with [`darglint`](https://github.com/terrencepreilly/darglint); security checks with [`safety`](https://github.com/pyupio/safety) and [`bandit`](https://github.com/PyCQA/bandit)
- Testing with [`pytest`](https://docs.pytest.org/en/latest/).

### Deployment features

- Everything is already set up for security checks, codestyle checks, code formatting, testing, linting, docker builds, etc with [`Makefile`](https://github.com/tjmillsco/python-ds-cookiecutter/blob/master/%7B%7B%20cookiecutter.project_name%20%7D%7D/Makefile#L89). More details in [makefile-usage](#makefile-usage).
- [Dockerfile](https://github.com/tjmillsco/python-ds-cookiecutter/blob/master/%7B%7B%20cookiecutter.project_name%20%7D%7D/docker/Dockerfile) for your package.

## How to use it

### Installation

To begin using the template consider updating `cookiecutter`

```bash
pip install -U cookiecutter
```

then go to a directory where you want to create your project and run:

```bash
cookiecutter gh:tjmillsco/python-ds-cookiecutter
```

### Input variables

Template generator will ask you to fill some variables.

The input variables, with their default values:

|     **Parameter**     |      **Default value**      | **Description**                                                                                                                                                               |
|:---------------------:|:---------------------------:|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `project_name`           | `python-project`            | [Check the availability of possible name](http://ivantomic.com/projects/ospnc/) before creating the project. |
| `project_description`    | based on the `project_name` | Brief description of your project. |
| `organization`           | based on the `project_name` | Name of the organization. We need to generate LICENCE and to specify ownership in `pyproject.toml`. |
| `license`                | `MIT`                       | One of `MIT`, `BSD-3`, `GNU GPL v3.0` and `Apache Software License 2.0`. |
| `minimal_python_version` | `3.7`                       | Minimal Python version. One of `3.7`, `3.8` and `3.9`. It is used for builds, GitHub workflow and formatters (`black`, `isort` and `pyupgrade`). |
| `github_name`            | based on the `organization` | GitHub username for hosting. Also used to set up `README.md`, `pyproject.toml` and template files for GitHub. |
| `email`                  | based on the `organization` | Email for `CODE_OF_CONDUCT.md`, `SECURITY.md` files and to specify the ownership of the project in `pyproject.toml`. |
| `version`                | `0.1.0`                     | Initial version of the package. Make sure it follows the [Semantic Versions](https://semver.org/) specification. |
| `line_length`            | 88                         | The max length per line (used for codestyle with `black` and `isort`). NOTE: This value must be between 50 and 300. |

All input values will be saved in the `cookiecutter-config-file.yml` file so that you won't lose them.

### More details

Your project will contain `README.md` file with instructions for development, deployment, etc. You can read [the project README.md template](https://github.com/tjmillsco/python-ds-cookiecutter/tree/master/%7B%7B%20cookiecutter.project_name%20%7D%7D) before.

### Initial set up

#### Initialize `poetry`

By running `make install`

After you create a project, it will appear in your directory, and will display [a message about how to initialize the project](https://github.com/tjmillsco/python-ds-cookiecutter/tree/master/%7B%7B%20cookiecutter.project_name%20%7D%7D#very-first-steps).
Want to know more about Poetry? Check [its documentation](https://python-poetry.org/docs/).

#### Initialize `pre-commit`

By running `make pre-commit-install`. Make sure to set up git first via `git init`.

### Makefile usage

[`Makefile`](https://github.com/tjmillsco/python-ds-cookiecutter/blob/master/%7B%7B%20cookiecutter.project_name%20%7D%7D/Makefile) contains a lot of functions for faster development.

<details>
<summary>1. Download and remove Poetry</summary>
<p>

To download and install Poetry run:

```bash
make poetry-download
```

To uninstall

```bash
make poetry-remove
```

</p>
</details>

<details>
<summary>2. Install all dependencies and pre-commit hooks</summary>
<p>

Install requirements:

```bash
make install
```

Pre-commit hooks coulb be installed after `git init` via

```bash
make pre-commit-install
```

</p>
</details>

<details>
<summary>3. Codestyle</summary>
<p>

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

<details>
<summary>4. Code security</summary>
<p>

```bash
make check-safety
```

This command launches `Poetry` integrity checks as well as identifies security issues with `Safety` and `Bandit`.

```bash
make check-safety
```

</p>
</details>

</details>

<details>
<summary>5. Type checks</summary>
<p>

Run `mypy` static type checker

```bash
make mypy
```

</p>
</details>

<details>
<summary>6. Tests</summary>
<p>

Run `pytest`

```bash
make test
```

</p>
</details>

<details>
<summary>7. All linters</summary>
<p>

Of course there is a command to ~~rule~~ run all linters in one:

```bash
make lint
```

the same as:

```bash
make test && make check-codestyle && make mypy && make check-safety
```

</p>
</details>

<details>
<summary>8. Docker</summary>
<p>

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

</p>
</details>

<details>
<summary>9. Cleanup</summary>
<p>
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

</p>
</details>

# Credit
Adapted from the fantastic https://github.com/TezRomacH/python-package-template template.