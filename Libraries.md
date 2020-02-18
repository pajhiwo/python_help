# Libraries




## Pandas
data structures and data analysis tools:

1.  Pandas.read_csv, pandas.read_json
2.  .loc["x1":"x2","y1":"y2"] - to get data, from range to range
3.  .iloc with indexes
4.  .ix(row index, column name)
5.  If index must be change .set_index(<Column name>)
6.  .drop(<name>,0 or 1) to delete data from date frame. 0 for rows, 1 for columns
7.  .T to transpone
    












# Changes & Config Management

## ConfigObject
Wrapper on top of ConfigParser with much easier api (but compatible with CP):  [https://pythonhosted.org/ConfigObject/#](https://pythonhosted.org/ConfigObject/#)

## Changelog CLI
Create and manage changlelog files from CLI: [https://pypi.org/project/changelog-cli/](https://pypi.org/project/changelog-cli/) in a format of [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)

# Builtin

## urllib.parse
Manage urls (also join with `urllib.parse.join`)

## pathlib
Can replace `os.path`. Allows to defines paths agnostic of underlying OS

## Pickle
* `dumps`: Accept python object and converts it into string and dumps it into a f
* `loads`: Retrieve python object from string

## Glob2
library for listing files, etc.

# Linters and formatters

## PyChecker
Detects bugs in python source code

## PyLint
Check if module meets coding standards

## Black
Code formatter: [https://github.com/psf/black](https://github.com/psf/black)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUyMTE4MDE5Nyw1MTYwNTkwMTUsLTEzNz
M1Nzg2OTYsMjEyNjk4NDUwNSw2NDI2MjU4MzJdfQ==
-->