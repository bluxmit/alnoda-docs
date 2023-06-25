# In-browser applications 

In-browser applications, also known as web applications, are programs that run directly within a web browser without needing 
to be installed in the workspace. 

!!! info
    In-browser applications necessitate no installation. All they require is a static file server in the workspace to be served.

!!! note
    Every Alnoda workspace has python static filke server by default, but you can also install other alternatives from the Aloda Hub.

The procedure of integrating static web applications into Alnoda workspaces involves two stages:

1. Downloading the static website that contains the in-browser application
2. Serving the downloaded static website via the static file server

As an example, let's add [__Laverna__](https://laverna.cc/index.html) to the workspace. Laverna is a JavaScript note-taking web application with a Markdown editor and encryption support. 
It's built to be an open source alternative to Evernote.

Open workspace terminal and download a prebuilt version of Laverna:

<div class="termy">
```bash
<font color="#5EA702">wget</font> https://github.com/Laverna/static-laverna/archive/gh-pages.zip -O laverna.zip
```
</div>

Extract zip file:

<div class="termy">
```bash
<font color="#5EA702">unzip</font> laverna.zip -d /home/abc/apps/
```
</div>

The files were extracted into the folder `/home/abc/apps/static-laverna-gh-pages/`, let's rename it:

<div class="termy">
```bash
<font color="#5EA702">mv</font> /home/abc/apps/static-laverna-gh-pages/ /home/abc/apps/laverna
```
</div>

Serve Laverna with a default python static server:

<div class="termy">
```bash
<font color="#5EA702">cd</font> /home/abc/apps/laverna; <font color="#5EA702">python</font> -m http.server 8026
```
</div>

Now you can open Limus using tab "My App on port 8026". 

!!! warning 
    In-browser applications store data not in the workspace, but in the browser you are opening it. If clear browser cache 
    you will loose the data. You will also not have the same data if you open app in the other browser. 