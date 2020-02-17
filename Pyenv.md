# Pyenv
Allows to install and use additional version of python.
If you have old version of python on yor OS do not upgrade (as OS may use system wide version for many apps), just install pyenv. 

### Supported OS
* Linux
* MacOS
* Windows (via pyenv-win fork)

### Installation
* install pyenv (requires `curl` and `git` to be already installed):
```bash
$ curl https://pyenv.run | bash
```
* install libraries allowing building python from source. On ubuntu:
```bash
sudo apt-get install -y make build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python-openssl
``` 
* add to `~/.zshrc` or `~/.bashrc`
```bash
export PATH="/home/kcz/.pyenv/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
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
pyenv allows to create and auto activate virtualenvs using `pyenv-virtualenv` plugin that is installed by installer.
It uses `.python-version` file to store info about virtualenv associated with given directory

* create virtualenv called: **project_x** using **3.8** python version (best practice: call virtualenvs like projects)
```bash
pyenv virtualenv 3.8 project_x
```
* and then  activate virtualenv (this will create file `.python_version` which is read by pyenv on entering dir and allows to automatically detect and activate venv)
```bash
pyenv local project_x
```
* list of virtualenvs
```bash
pyenv virtualenvs
```
* delete virtualenv called project_x
```bash
pyenv virtualenv-delete project_x
cd <project_dir>
rm .python-version
```


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM4MjM3ODQ2NSwtOTM0NDY3Nzg0LDQ2MD
gyNDkwOSwxODg5OTkzMzQwXX0=
-->