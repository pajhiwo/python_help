## Pyenv
Allows to install and use additional version of python.
If you have old version of python on yor OS do not upgrade (as OS may use system wide version for many apps), just install pyenv. 

### Supported OS
* Linux
* MacOS
* Windows (via pyenv-win fork)

### Installation
* install pyenv:
```bash
$ curl https://pyenv.run | bash
```
* install libraries allowing building python from source. On ubuntu:
```bash
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python-openssl git
``` 
* restart shell
```bash
exec $SHELL
```
### Usage
* update
```bash
pyenv update
```
* remove
```bash
rm -rf ~/.pyenv
```
remove entries from ~/.bashrc
```bash
export PATH="$HOME/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
```
* list available python version
```bash
pyenv install --list
```
* list installed python version
```bash
pyenv versions
```
* install python version (i.e. 3.8)
```bash
pyenv install 3.8
```
* set version as global (i.e. 3.8)
```bash
pyenv global 3.8
```
* set version as local (i.e. 3.8)
```bash
pyenv local 3.8
```
### Virtualenv
pyenv allows to create and auto activate virtualenvs using pyenv-virtualenv plugin that is installed by installer.

* create virtualenv **project_x** using **3.8** python version. Name virtualenvs like projects
```bash
pyenv virtualenv 3.8 project_x
```
* Activate virtualenv
```bash
pyenv local project_x
```
### ZSH


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUwNjgzNjAwNSwxMDU2MjI1NDcwLC0xNT
M2NTM4NzA5LC0xNDIyODA4OTQ0LC0xNDM0MTQ1NTgwXX0=
-->