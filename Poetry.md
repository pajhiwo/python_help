# Poetry
Poetry is a tool for dependency management and packaging in Python.

## Installation
Unix
```bash
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python
```
Windows (powershell)
```
(Invoke-WebRequest -Uri https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py -UseBasicParsing).Content | python
```

1. poetry new myproject
2. cd myproject
3. pyenv virtualenv myproject
4. pyenv local myproject
5. 

install new module (like pip install), also as dev dependency
```bash
poetry add [--dev] <package>
```
setup.py == pyproject.toml
install package dependencies into venv from `poetry.lock`
```bash
 poetry install
 ```
 Show installed packages and location of virtualenv
```bash
poetry show -v
 ```
 remove installed package (also from dev)
```bash
poetry remove [--dev] package
```
Spawn new shell with venv (if no venv creates one)
```bash
poetry shell
```
install app into venv (i.e. pip install -e)
```bash
poetry build
poetry install
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NTk4MTEyMTNdfQ==
-->