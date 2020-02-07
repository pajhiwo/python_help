# Poetry
In general `poetry` tries to replace pip, setup.py and build tools used to build python and put them into index (i.e. pypi).

## Installation
Unix
```bash
curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python
```
Windows (powershell)
```
(Invoke-WebRequest -Uri https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py -UseBasicParsing).Content | python
```
### Create project with `poetry` and `pyenv`


1. poetry new myproject
2. cd myproject
3. pyenv virtualenv myproject
4. pyenv local myproject
5. 
6. 
### Virtualenvs location
```bash
 $HOME/.cache/pypoetry/virtualenvs
```
setup.py == pyproject.toml

### Install package dependencies into venv from `poetry.lock`
```bash
 poetry install
 ```
### Show installed packages and location of virtualenv
```bash
poetry show -v
 ```
 ### Remove installed package (also from dev)
```bash
poetry remove [--dev] package
```
### Spawn new shell with venv (if no venv creates one)
```bash
poetry shell
```
### install app into venv (i.e. pip install -e)
```bash
poetry build
poetry install
```
### Change python version in venv
* option 1:
```bash
# Change in pyproject.toml version of py to desired: python = "^2.7"
pyenv install 2.7.15
pyenv local 2.7.15  # Activate Python 2.7 for the current project
poetry install
# Change env path in PyCharm
```
* option2:
```bash
poetry env use /full/path/to/python
```

### Port poetry requirements to pip's requirements.txt
```bash
poetry export -f requirements.txt > requirements.txt
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTIzMTI0MTQxNCwtNDM3MDM5NTAwLC0xNj
U5ODExMjEzXX0=
-->