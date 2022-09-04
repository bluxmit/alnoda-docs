<p align="center">
  <img src="./img/python-circle.svg" alt="Python logo" width="150">
</p>  

# Python workspace 

Containerized isolated development environment for Python.  

## Why this images

1. If you need self-hosted remote development environment.
2. If you want to be one command away from coding in Python.

## Start
 
```
docker run --name space-1 -d -p 8020-8040:8020-8040 alnoda/python-workspace
```  

and open [localhost:8020](http://localhost:8020) in browser.  

## Features

**Python tools:**

- [IPython and Notebooks](https://ipython.readthedocs.io/en/stable/)
- [Pdoc3](https://github.com/pdoc3/pdoc)
- [Pytest-html-reporter](https://github.com/prashanth-sams/pytest-html-reporter)
- [SnakeViz](https://jiffyclub.github.io/snakeviz/)
- [Vprof](https://github.com/nvdv/vprof)
- [Pyinstrument](https://pypi.org/project/pyinstrument/3.0.0b3/)
- [Flameprof](https://github.com/baverman/flameprof/)
- [Pylint-json2html](https://github.com/Exirel/pylint-json2html)
- [Pre-commit](https://pre-commit.com/)
- [Flake8](https://flake8.pycqa.org/en/latest/)
- [Poetry](https://python-poetry.org/)
- [Black](https://github.com/psf/black)

**Dev tools:**

- [**Eclipse Theia**](https://theia-ide.org/docs/) - open source version of popular Visual Studio Code IDE. Theia is trully open-source, has 
VS-Code extensions and works in browser. This means it can run inside a docker container on local machine or in cloud. A lot of beautiful color themes and many common plugins are already installed to save time.
- [**Terminal**](https://github.com/tsl0922/ttyd) - secure browser-based terminal.
- [**FileBrowser**](https://github.com/filebrowser/filebrowser)  - manage files and folders inside the workspace, and exchange data between local environment and the workspace
- [**Ungit**](https://github.com/FredrikNoren/ungit) - rings user friendliness to git without sacrificing the versatility of it.
- **Ubuntu 20.4** with the following CLI apps
    - [Zsh](https://www.zsh.org/), [Oh my Zsh](https://ohmyz.sh/)
    - Python 3, Pip 
    - Node/nodeenv
    - curl, wget, telnet, jq
    - **Git:** git, git-flow, lazygit 
    - **File browsers:** mc
    - **Text editors:** nano, vim, mcedit
    - **System monitors:** ncdu, htop, glances, vizex
    - **Process Control:** supervisord
    - **Job scheduler:** cron
    - **Terminal multiplexer:** tmux 

