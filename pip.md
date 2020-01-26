# Pip
`pip` is package manager for python
## Installation
* should be included in 3.4 and 2.7.9 python instaallers
* or download: 
	* `curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py`
	* install using `python<version> get-pip.py`
## Usage
### ==python\<version> -m pip==
* always call pip by as module (allows to update pip on Win)
* specify python version - be sure where package is installed e.g.
```bash
python3.8 -m pip install -U requests
```
* install package from other index (i.e. not pypi)
* install package to given dir
* install from requirements file
* install from 
* remove package
* remove package and all its dependencies
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNDQ3OTUwNzZdfQ==
-->