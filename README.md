# pyenv_pipenv_quickset
## Pyenv setting
(Stolen from Imai san's instruction)
```
# install pywnv
cd ~
git clone https://github.com/yyuu/pyenv.git ~/.pyenv
echo 'export PYENV_ROOT="${HOME}/.pyenv"' >> ~/.bash_profile
echo 'if [ -d "${PYENV_ROOT}" ]; then' >> ~/.bash_profile
echo 'export PATH=${PYENV_ROOT}/bin:$PATH' >> ~/.bash_profile
echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
echo 'fi' >> ~/.bash_profile

# active now bash setting
source ~/.bash_profile

# list all available python 3.6.X versions
pyenv install --list|grep 3.6

# install python 3.6.6
pyenv install 3.6.6
```
In the project folder
```
# set and check the python and pip version for the project
pyenv global 3.6.6  # set python 3.6.6 as the general default python
pyenv local 3.6.6 #set python 3.6.6 as project default python

# check the version
python --version
pip --version
```

## [Pipenv](https://pipenv.readthedocs.io/en/latest/#)
or check *[other pkg control tools](https://docs.python-guide.org/dev/virtualenvs/)*
```
# install pipenv
pip install pipenv
```
*(optional)* Set project folder as default dir for virtualenv<br/>
```
echo 'export PIPENV_VENV_IN_PROJECT=1' >> ~/.bash_profile
```
--> then the environment would be in `{the_project}/.venv`<br/>
---> else in `~/.virtualenvs`

In the project folder:
```
pipenv install --> if `Pipfile` exist, install it; else create an initial Pipfile
pipenv shell
```
This will bring up a terminal in your virtualenv like this:
```
(my-virtualenv-name) bash-4.4$
```

### Install and uninstall Pkg
```
# in project virtualenv
# install
pipenv install the-target-pkg
# uninstall
pipenv uninstall the-target-pkg
```

### set the virtual enviroment as a notebook kernal
In the virtual enviroment shell do:
```
pipenv install ipykernel

# install kernal
python -m ipykernel install --user --name=my-virtualenv-name

# Launch jupyter notebook:
jupyter notebook
```


In your notebook, `Kernel` -> `Change Kernel`.<br/> The new kernel should now be an option.

Double check if the kernel exist:<br/>
```
ls /Users/yingmingchen/Library/Jupyter/kernels
```
