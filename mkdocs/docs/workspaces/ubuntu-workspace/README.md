# Ubuntu workspace
Containerized Linux terminal environment. Essentially Ubuntu 20.04 docker image extended with typical console apps, such as Git, 
file browsers and system monitors.

![Workspace collage](img/ubuntu-wid-collage.png)

## Why this image

If you need to isolate some work without polluting main environment.

## Start

```
docker run --name space-1 -d alnoda/ubuntu-workspace
```

Enter workspace

```
docker exec -it --user=root space-1 /bin/zsh
```

## Features

- **Ubuntu 20.4** with the following CLI apps
    - [Zsh](https://www.zsh.org/), [Oh my Zsh](https://ohmyz.sh/)
    - Python 3, Pip 
    - Node/nodeenv
    - curl, wget, telnet, jq
    - **Git:** git, git-flow, lazygit 
    - **File browsers:** mc, xplr
    - **Text editors:** nano, vim, mcedit
    - **System monitors:** ncdu, htop, glances, vizex
    - **Process Control:** supervisord
    - **Job scheduler:** cron


<div align="center" style="font-style: italic;">
    Demo: Ubuntu-workspace
</div>

![sen-demo](img/ubuntu-workspace.gif)



