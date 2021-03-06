# Tools
## Formatters
* [isort](https://pycqa.github.io/isort/) - sorts the imports. Supports running from code.Does n
* [black](https://github.com/psf/black) - formats the code, vary little config options, other tools should be configured to apply black formatting rules (like isort). Does not support running from code
* [autopep8](https://github.com/hhatto/autopep8) - formats the code like black. Much more config options. Supports running from code.

all of them supports the config in `pyproject.toml`
## Linters
* [flake8](https://flake8.pycqa.org/en/latest/) - linter checking code according to PEP8 and with support for plugins:
	* black (flake8-black)
	* isort (flake8-isort)

does not support config in `pyproject.toml`. Config has to be placed in `.flake8` file

# Including in the pipeline
Using PyCharm is not a go as it cannot be used in CI. Script that can do 2 things:
* check linting using flake8 with  plugins. To be run in CI and fails the job/stage if there are some issues in formatting found
*  fix linting by applying imports formatting and whole codebase formatting

It can be achieved using flake8 for checking, black and isort for formatting.
* isort used from code using:
```python
        # need to pass config loaded into var as currently 'quiet' read directly from toml in isort.file does not work:
        # https://github.com/PyCQA/isort/issues/1461
        isort_config = isort.Config(settings_file=CodeFormatter.PYPROJECT_TOML_PATH)
        is_fixed_isort = isort.file(pyfile, config=isort_config)
  ```
* black using subprocess. Capture all output and decide if it there were some formatting performed:
```python
_, err = subprocess.Popen(["black", pyfile], stdout=subprocess.PIPE, stderr=subprocess.PIPE).communicate()
        is_fixed_black = True if "1 file reformatted" in str(err) else False
```

## Config
`pyproject.toml`:
```toml
[tool.isort]
sections = "FUTURE,STDLIB,THIRDPARTY,FIRSTPARTY,LOCALFOLDER"
known_first_party = "our_module"
case_sensitive = true
quiet = true
# settings below to comply to black formatting rules
multi_line_output = 3
include_trailing_comma = true
force_grid_wrap = 0
use_parentheses = true
ensure_newline_before_comments = true
line_length = 120

[tool.black]
line_length = 120
target-version = ['py36']
```
---
`flake8`:
```toml
[flake8]
max-line-length = 120
max-complexity = 10
```Solutions
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NDg5NjA4NTNdfQ==
-->