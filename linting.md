# Tools
## Formatters
* [isort](https://pycqa.github.io/isort/) - sorts the imports. Supports running from code.
* [black](https://github.com/psf/black) - formats the code, vary little config options, other tools should be configured to apply black formatting rules (like isort). Does not support running from code
* [autopep8](https://github.com/hhatto/autopep8) - formats the code like black. Much more config options. Supports running from code.

all of them supports the config in `pyproject.toml`
## Linters
* [flake8](https://flake8.pycqa.org/en/latest/) - linter checking code according to PEP8 and with support for plugins:
	* black (flake8-black)
	* isort (flake8-isort)

does not support config in `pyproject.toml`. Config has to be placed in `.flake8` file

# Including in the pipeline
Using PyCharm is not a go as it cannot be used in CI 
1. Script that can do 2 things:
	* check linting using flake8 with  plugins. To be run in CI and fails the job/stage if there are some  
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM4ODQzNTE5NSwtMTkxMDA2NTY5MywtMj
A4ODc0NjYxMl19
-->