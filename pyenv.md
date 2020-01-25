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
* install python version (i.e. 3.8)
pyenv install 3.8
* set version as global (i.e. 3.8)
pyenv global 3.8
* set version as local (i.e. 3.8)
pyenv local 3.8

### Virtualenv
* create virtualenv **project_x** using **3.8** python version (if pyenv-vrutalenv plugin isntalled - installer installs it)
pyenv virtualenv 3.8 project_x


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTA1NjIyNTQ3MCwtMTUzNjUzODcwOSwtMT
QyMjgwODk0NCwtMTQzNDE0NTU4MF19
-->