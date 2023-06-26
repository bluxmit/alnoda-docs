# Wrk 

wrk is a command-line interface (CLI) tool that offers an alternative to using Workspace Admin for managing workspace features. 

The wrk tool can be utilized for creating workspace provisioning scripts, within Dockerfiles, and in Alnoda Hub app installation scripts.


## id 

_Command_: `wrk id` 

_Description:_ Display the workspace id

<div class="termy">
```
$ wrk id
 
dhfoeahbslahinbk
```
</div>


## signin

_Command:_: `wrk signin '[security token]'`   

_Description:_ Authenticate workspace at alnoda.org  

_Parameters:_  

- token (str): personal security token from Alnoda Hub  
    
<div class="termy">
```
$ wrk signin 'hf$HvypaBw&)U!^1Y%Kgp&$4TjT98dh^7))SMB79'
 
✨ Hello username!
```
</div>

!!! warning 
    Wrap your token with single quotes


## signout

_Command:_: `wrk signout`  

_Description:_ Log out workspace from alnoda.org  

<div class="termy">
```
$ wrk signout
 
👋 Goodbye!
```
</div>


## descr 

_Command:_ `wrk descr`  

_Description:_ Edit interactively the workspace description using the command-line text editor, mcedit.


## update

_Command:_ `wrk update [what] '[new value]'`  

_Description:_ Update workspace meta (name, version, author or description)

_Parameters:_

- what (str): element of metadata to update. Allowed values: _name_, _version_, _author_, _description_ (default)  
- value (str): new value

<div class="termy">
```
$  wrk update name 'My awesome workspace'
 
✅ Done!
```
</div>


## start 

_Command:_ `wrk start [service name] '[start command]'` 

_Description:_ Start persisten application or service (as a daemon).

_Parameters:_ 

- name (str) - service name 
- cmd (str) - command to start a service 

<div class="termy">
```
$ wrk start statichome 'cd /home/project/; python -m http.server 8026'
 
✅ Done!
❗ Service activation requires workspace reboot!
```
</div>


## stop
_Command:_ `wrk stop [service name]` 

_Description:_ Stop service.  

_Parameters:_ 

- name (str) - service name 

<div class="termy">
```
$ wrk stop statichome
 
✅ Done!
❗ Workspace reboot is required!
```
</div>


## apps 

_Command:_ `wrk apps` 

_Description:_ Display installed apps from Alnoda Hub.

<div class="termy">
```
$ wrk apps
 
❇️ code-server
Name:        Code-server
Version:     4.13.0
Description: VS Code IDE (code editor) in browser
❇️ poetry
Name:        Poetry
Version:     1.4.0
Description: Python packaging and dependency management made easy
```
</div>


## install

_Command:_ `wrk install [app name] [tab]` 
    
_Description:_ Install an app from Alnoda Hub.

_Parameters:_

- application (str) - application name from Alnoda Hub
- tab (str) - workspace UI tab where the app shortcut will be placed, default - Home tab.

<div class="termy">
```
$ wrk install postgresql
 
✨ starting...
⚠️ Please DO NOT close this terminal window untill app is fully installed!
➡️ checking workspace compatibility...
➡️ checking app compatibility...
➡️ executing installation script...
✔️ app installed
➡️ setting startup configuration...
-------------------------------------------------------------
- ⚠️ application will start after workspace is restarted ⚠️  -
---       restart workspace with    'wrk kill'             ---
-------------------------------------------------------------
➡️ adding workspace tags...
❗ Could not update workspace app history at alnoda.org: Not authenticated at alnoda.org
✍️ If app is not working try restarting terminal window or entire workspace
🚀 done
R E S T A R T    T E R M I N A L    N O W   (CTRL+D) !!!!!!!!
***********************************************
psql
***********************************************
```
</div>


## setvar

_Command:_ `wrk setvar [name] '[value]'` 

_Description:_ Set terminal shell (zsh) environmental variable. Same as 'wrk env'.

_Parameters:_

- name (str) - name of the environmental variable
- value (str) - value of the environmental variable

<div class="termy">
```
$ wrk setvar MY_NEW_VAR 'my new environmental variable' 
 
✅ Done!
❗ Terminal reload is required!
```
</div>

!!! warning 
    Wrap variable value with single quotes!


## env

_Command:_ `wrk env [name] '[value]'` 

_Description:_ Set terminal shell (zsh) environmental variable. Same as 'wrk setvar'.

_Parameters:_

- name (str) - name of the environmental variable
- value (str) - value of the environmental variable

<div class="termy">
```
$ wrk env MY_NEW_VAR 'my new environmental variable' 
 
✅ Done!
❗ Terminal reload is required!
```
</div>


## addpath

_Command:_ `wrk addpath '[folder]'` 
    
_Description:_ Add a folder to PATH, only applies to terminal zsh shell.

_Parameters:_

- folder (str) - folder that should be added to PATH.

<div class="termy">
```
$ wrk addpath '/home/project/'
 
✅ Done!
❗ Workspace reboot is required!
```
</div>


## alias

_Command:_ `wrk alias [name] '[cmd]'` 

_Description:_ Set alias for zsh terminal shell (name='value').

_Parameters:_

- name (str) - alias
- cmd (str) - command

<div class="termy">
```
$ wrk alias ps 'ps axf' 
 
✅ Done!
❗ Workspace reboot is required!
```
</div>


## cheatsec

_Command:_ `wrk cheatsec '[name]'` 
    
_Description:_ Add a section to the cheatsheet tab. 

<div class="termy">
```
$ wrk cheatsec 'React'
 
✅ Done!
```
</div>


## cheat

_Command:_ `wrk cheat '[section]' '[cmd]' '[description]'` 

_Description:_ Add cheatsheet command to some section.

_Parameters:_

- section (str) - section to add note to 
- cmd (str) - command 
- description (str) - description 

<div class="termy">
```
$ wrk cheat React 'npx create-react-app my-app' 'bootstrap a new React application in a directory named my-app.' 
 
✅ Done!
```
</div>


## linksec

_Command:_ `wrk linksec '[name]'` 
    
_Description:_ Add a section to the links.

_Parameters:_

- name (str) - Name of a new section on the Links tab.

<div class="termy">
```
$ wrk linksec 'React'
 
✅ Done!
```
</div>


## link

_Command:_ `wrk link '[section]' '[url]' '[name]' '[description]'` 
    
_Description:_ Add new link to the existing link section.

_Parameters:_

- section (str) - section name 
- url (str) - link URL
- name (str) - link name
- description (str) - description

<div class="termy">
```
$ wrk link 'React' 'https://react.dev/learn' 'React docs' 'React documentation'
 
✅ Done!
```
</div>


## kill

_Command:_ `wrk kill` 

_Description:_ Kill (and restart) the workspace.

<div class="termy">
```
$ wrk kill
 
⚠️ WARNING: this will stop the workspace.
Do you want to continue❓ [y/N]: 
```
</div>


## upgrade

_Command:_ `wrk upgrade` 

_Description:_ Upgrade wrk version.

<div class="termy">
```
$ wrk upgrade
 
Current version 0.4.21
New version available 0.4.22. Do you want to upgrade❓ [y/N]:
```
</div>


## help 

_Command:_ `wrk --help`  

_Description:_ Show the help documentation for `wrk` tool in the terminal shell.
