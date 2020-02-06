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

install new module (like pip install)
poetry add <package>
install new module to development dependencies (i.e. linters)
poetry add --dev <package>
setup.py == pyproject.toml
install developed package into venv (i.e. pip install -e)
 poetry install
 Show installed packages and location of virtualenv
 poetry show -v



> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzgzMDc0OTYsLTIwODgyNDA3MTQsMjEyNz
AzODk3MSwzMDU2NzUyMjYsLTE5MDQ1OTQ0MzBdfQ==
-->