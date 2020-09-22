# Tools
## Formatters
* [isort](https://pycqa.github.io/isort/) - sorts the imports
* [black](https://github.com/psf/black) - formats the code, vary little config options, other tools should be configured to apply black formatting rules (like isort)
* [autopep8](https://github.com/hhatto/autopep8) - formats the code like black. Much more config options

all of them supports the config in `pyproject.toml`
## Linters
* [flake8](https://flake8.pycqa.org/en/latest/) - linter checking code according to PEP8 and with support for plugins:
	* black
does not support config in pyproject.toml. Config has to be placed in `.flake8` file
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA5Mzk2Mzg4NywtMTkxMDA2NTY5MywtMj
A4ODc0NjYxMl19
-->