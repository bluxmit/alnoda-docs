# ASDF plugins

[__ASDF__](https://asdf-vm.com/) (Another System Definition Facility) is a version manager for handling multiple versions of languages, packages, or any binary 
tools on a per-project basis. It's a versatile tool for developers to manage their software environment. With ASDF, you can easily 
switch between different versions of a package, depending on the project requirements.

!!! info 
    Asdf is istalled by default in every Alnoda workspace. 

Installing a Package with ASDF: Before you can install a package, you need to install its plugin.  

List asdf plugins:

<div class="termy">
```
<font color="#5EA702">asdf</font> plugin list all 
```
</div>


For example, if you want to install Node.js, you would first install the Node.js plugin:

<div class="termy">
```
<font color="#5EA702">asdf</font> plugin-add nodejs
```
</div>

Display installed plugins:

<div class="termy">
```
$ asdf plugin list --urls 

nodejs   https://github.com/asdf-vm/asdf-nodejs.git
```
</div>

Now you can install a specific version of Node.js:

<div class="termy">
```
$ asdf install nodejs 14.15.1

Cloning node-build...
Downloading node-v14.15.1-linux-x64.tar.gz...
-> https://nodejs.org/dist/v14.15.1/node-v14.15.1-linux-x64.tar.gz
WARNING: node-v14.15.1-linux-x64 is in LTS Maintenance mode and nearing its end of life.
It only receives *critical* security updates, *critical* bug fixes and documentation updates.
Installing node-v14.15.1-linux-x64...
Installed node-v14.15.1-linux-x64 to /home/abc/.asdf/installs/nodejs/14.15.1
```
</div>

Finally, set the version of Node.js you want to use:

<div class="termy">
```
<font color="#5EA702">asdf</font> global nodejs 14.15.1
```
</div>

Now you can verify that Node.js was installed correctly:

<div class="termy">
```
$ node -v

v14.15.1
```
</div>
