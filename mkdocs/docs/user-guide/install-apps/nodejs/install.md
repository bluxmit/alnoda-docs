# Node.js 

GitHub and NPM offer an extensive collection of applications, including both command-line interface (CLI) tools and those with 
browser-based user interfaces. Adding Node.js applications to Alnoda workspaces is relatively straightforward. 

## Nodeenv

To utilize Node.js applications in Alnoda workspaces, the appropriate version of Node.js with npm or yarn must be installed. 
Due to the different version requirements of various applications, each should be installed in its own isolated environment. 
Alnoda workspaces are equipped with [__nodeenv__](https://github.com/ekalinin/nodeenv) by default.

Nodeenv simplifies the process by enabling the creation of a localized version of Node.js, npm or yarn within a distinct folder.

Create virtual environment with a specific version of Node.js: 

<div class="termy">
```
<font color="#5EA702">nodeenv</font> --node=16.16.0 env
```
</div>

Activate virtual environment: 

<div class="termy">
```
. env/bin/activate
```
</div>

## npm

Once the necessary Node.js version is set up in an isolated local environment, we can proceed to install the application. 
The simplest way is installing applications directly from the NPM.

Installing applications from NPM is easier. For example install the `express-generator`:

<div class="termy">
```
<font color="#5EA702">npm</font> install -g express-generator
```
</div>

## From source 
You can also clone remote Git repository, followed by installing the dependencies and building it. For example, let's install 
a markdown editor called "StackEdit" from a Git repository.

First restart terminal to deactivate any nodeenv environment, and clone the "StackEdit" repository:

<div class="termy">
```
<font color="#5EA702">git</font> clone https://github.com/benweet/stackedit.git /home/abc/apps/stackedit
```
</div>

Navigate into the cloned repository's directory and install node environment with the specific Node.js version: 

<div class="termy">
```
<font color="#5EA702">cd</font> stackedit
<font color="#5EA702">cd</font> /home/abc/apps/stackedit && <font color="#5EA702">nodeenv</font> --node=12.13.0 env && . env/bin/activate
```
</div>

Install the npm dependencies:

<div class="termy">
```
<font color="#5EA702">npm</font> install
```
</div>

Once the dependencies are installed, you can start the application with:

<div class="termy">
```
<font color="#5EA702">npm</font> start
```
</div>

The application will be served on port 8080 (at the time of writing this doc). Port 8080 is not exposed by the workspace and 
we need to forward it to the exposed port 

<div class="termy">
```
<font color="#5EA702">socat</font> tcp-listen:8026,reuseaddr,fork tcp:localhost:8080
```
</div>

Now you can open StackEdit Box from the tab "My App on port 8026"

!!! tip 
    Explore this document further for additional examples of installing Node.js applications
