# ZeroDivs  - UI Editor for CSS Illustrations

## Intro

In this example we will set up [__ZeroDivs__](https://github.com/jperals/zerodivs) in the workspace.    

ZeroDivs - is a UI Editor for creating CSS illustrations with a single HTML element 

!!! attention
    ZeroDivs can be installed in any workspace. We will use __Node workspace v.4.0__ in this example.

!!! note
    We will create isolated node environment for ZeroDivs and its dependencies.  
    Then we will start it in a permanent way, and add ZeroDivs tab shortcut to the workspace UI. 


## Prepare  

First thing is to install python2. ZeroDivs has rather outdated dependencies. 
Luckily workspace is completely isolated, and this won't affect you main environment.  

Open workspace terminal and execute the next commands

<div class="termy">
```bash
$ sudo apt-get update
$ sudo apt-get install -y python2

Preparing to unpack .../python2_2.7.17-2ubuntu4_amd64.deb ...
Unpacking python2 (2.7.17-2ubuntu4) ...
Setting up libpython2.7-stdlib:amd64 (2.7.18-1~20.04.3) ...
Setting up python2.7 (2.7.18-1~20.04.3) ...
Setting up libpython2-stdlib:amd64 (2.7.17-2ubuntu4) ...
Setting up python2 (2.7.17-2ubuntu4) ...
Processing triggers for mime-support (3.64ubuntu1) ...
```
</div>


## Install 

Open workspace terminal, clone ZeroDivs git repository and enter it

<div class="termy">
```bash
$ git clone https://github.com/jperals/zerodivs /home/abc/apps/zerodivs

Cloning into '/home/abc/apps/zerodivs'...
remote: Enumerating objects: 1915, done.
remote: Counting objects: 100% (319/319), done.
remote: Compressing objects: 100% (174/174), done.
remote: Total 1915 (delta 159), reused 256 (delta 138), pack-reused 1596
Receiving objects: 100% (1915/1915), 3.55 MiB | 13.08 MiB/s, done.
Resolving deltas: 100% (1336/1336), done.

$ cd /home/abc/apps/zerodivs
with <font color="#FDEB61">abc</font> in <font color="#37E6E8">/home/abc/apps/zerodivs</font> on <font color="#BC94B7">⇡master</font> <font color="#98E242">➜</font>
```
</div>

Create node enviroment and activate it

<div class="termy">
```
$ nodeenv --node=12.18.3 env && . env/bin/activate

 * Install prebuilt node (12.18.3) ..... done.
(env) 19:58:14 with <font color="#FDEB61">abc</font> in <font color="#37E6E8">/home/abc/apps/zerodivs</font> on <font color="#BC94B7">⇡master</font> is 📦  <font color="#5EA702">via ⬢ v12.18.3</font>  <font color="#98E242">➜</font>
```
</div>


Local project setup

<div class="termy">
```
$ npm install

...
added 1702 packages from 1562 contributors and audited 1704 packages in 46.76s
```
</div>


Install http-server

<div class="termy">
```
$ npm install http-server -g

+ http-server@14.1.1
added 39 packages from 43 contributors in 4.852s
```
</div>

Build ZeroDivs 

<div class="termy">
```
$ npm run build

...
Search for the keywords to learn more about each warning.
To ignore, add // eslint-disable-next-line to the line before.
```
</div>


## Run

Start the http-server

<div class="termy">
```
$ cd dist && http-server -p 8030

...
Search for the keywords to learn more about each warning.
To ignore, add // eslint-disable-next-line to the line before.
```
</div>












## Add to workspace

We can use Neuromorphism now. But it was started from the terminal. As soon as we close the terminal, Neuromorphism process will terminalte. 
It is inconvenient to start Neuromorphism via terminal command (together with socat) every time we want to use it.  

It would be more convenient if we didn't have to start Neuromorphism from the terminal each time. Neuromorphism should start 
automatically with all other workspace applications every time we start the workspace.     

Let's add Neuromorphism as a permanent workspace application: 

- [X] Open "Admin" tab oo the workspace UI and avigate to "Workspace Settings" 
- [X] Go to the tab "Apps & Services"
- [X] Select "START NEW" from the picklist 
- [X] Enter the following command 

```
cd /home/abc/apps/neumorphism; . env/bin/activate; npm start
``` 
This command consists of 3 parts: 1) go to the Neumorphism repo, 2) activate node environment, 3) start Neumorphism

- [X] Give it any name you want 
- [X] Click "Save"

![neumorphism-start](img/neumorphism-start.jpg)

Now let's create service for the port tuneling as well

- [X] Select "START NEW" from the picklist 
- [X] Enter the following command 

```
socat tcp-listen:8032,reuseaddr,fork tcp:localhost:3000
``` 
This time we will forward traffic from port 3000 to 8032 - one of the workspace free ports.

- [X] Give it any name you want 
- [X] Click "Save"

![neumorphism-port](img/neumorphism-port.jpg)

Please restart workspace to apply changes.


## Create UI tab 

Let's add Neumorphism shortcut tab to the workspace "Home" page.   

Shortcut tab has title, description and image. Use filebrowser or IDE to upload any image you want into the workspace. 
You can choose whatever you like, one option - is to create a printscreen of the Neumorphism app itself.  

After you upload the image to the workspace

- [X] Go to the "Interface" tab of the workspace settings and select "CREATE NEW" from the picklist.   
- [X] Give it any title and description. 
- [X] In the field "Port" enter port 8032 - the port we used to forward traffic from port 3000
- [X] In the file picker find your image.   
- [X] Leave field "path" blank and click "Create"

![neumorphism-ui](img/neumorphism-ui.jpg)

Now we have Neumorphism tab on the Home page 

![neumorphism-home](img/neumorphism-home.jpg)

## Result

Neumorphism was installed and permanently added to the workspace. If we stop and then start workspace, neumorphism will start too.  
