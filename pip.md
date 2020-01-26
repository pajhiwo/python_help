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
python3.8 -m pip install -U r
```
* install from local src in order to check currently developed project
```bash
pip install -e <path>
```
* install package from other index (i.e. not pypi)
```bash
pip install --index-url http://my.package.repo/simple/ SomeProject
```
* install package to given dir
```bash
pip install --install-option="--prefix=$PREFIX_PATH" package_name
```
* install package from local HD
```bash
pip install <path>
```
* install from requirements file
```bash
pip install -r requirements.txt
```
* remove package
```bash
pip uninstall package_name
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI0MzU4NDQxOV19
-->