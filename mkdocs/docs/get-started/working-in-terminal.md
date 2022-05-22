
For convenient use of CLI applications, workspaces have full-screen browser-based terminal.  

Workspace is based on Ubuntu 20.04 with many typical CLI applications pre-installed, such as Git, Vim, Nano and Curl.  

## Install new applications

Open workspace terminal to install new applications. 
Simply execute `apt install` with `sudo`.  

For example, install emacs 

```sh
sudo apt-get install emacs
```

If you want to install PHP, execute

```sh
sudo add-apt-repository ppa:ondrej/php
sudo apt-get update
sudo apt-get install php8.1
```

## Python
Python and Pip are installed. Execute `python3` in terminal.  

To install python packages use PIP

```
pip install pandas
```

## Node.js
Use Nodeenv to create Node.js environments.  

For example, open workspace terminal, create folder npmgui, and activate environment with node v.12.18.3 and npm v.6.0.0

```
cd /home
mkdir npmgui; cd npmgui  
nodeenv --node=12.18.3 --npm=6.0.0 env
```

Let's install package and start node application, explicitly on port 8040

```
. env/bin/activate && npm i -g npm-gui   
npm-gui 0.0.0.0:8040
```

In the Quicklaunch go to the tab 'My apps' and open app on the port 8040. 

> **NOTE:** If you close terminal, the application will stop. If you want application to keep running after workspace terminal is closed 
start it with **"&!"** at the end. 

![Quickstart page](img/start-app.gif)

## Keep services runnning

Any application started in the terminal will run as long as your terminal session is alive. 
If you want any application or service runing after terminal session is closed, start service with **"&!"** at the end of 
the command.  

For example, to start *npm-gui* and keep it running after terminal is closed, run 

```
npm-gui 0.0.0.0:8040 &!
```   
