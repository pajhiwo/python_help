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
pyenv install --list
* list installed python version
pyenv versions
* install python version
* set version as global
* set version as 

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0OTc2MDAyMjcsLTE1MzY1Mzg3MDksLT
E0MjI4MDg5NDQsLTE0MzQxNDU1ODBdfQ==
-->