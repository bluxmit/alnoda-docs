### Pyenv

[pyenv](https://github.com/pyenv/pyenv) is used to isolate Python versions. For example, you may want to test your code against 
Python 2.7, 3.6, 3.7 and 3.8, so you'll need a way to switch between them. 

List python versions

```
pyenv install --list
```

Install additional python versions

```
pyenv install 3.10.4
pyenv install  3.6.0
```

Check installed python versions

```
pyenv versions
```

Change global python version 

```
pyenv global 3.10.4
```

Check python version

```
python --version
```

Create folder with local python environment, check Python version

```
mkdir test-pyenv
cd test-pyenv
pyenv local 3.6.0
python --version
```

If you want to schedule script (with Cronicle) that uses pyenv, add `eval "$(pyenv init -)"` before the script. 
For example `eval "$(pyenv init -)"; python /home/project/scripts/script.py`
