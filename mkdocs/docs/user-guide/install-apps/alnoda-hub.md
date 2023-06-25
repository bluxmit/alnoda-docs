# Alnoda Hub

The Alnoda Hub simplifies the process of installing applications in workspaces. When utilizing the Hub for installations, you don't 
need to concern yourself with service start-ups, home page shortcut creation, or environmental variable setting. Even workspace 
features like tags, aliases, and links are conveniently updated for you. This seamless process helps you to configure workspace fast.

!!! info
    Aloda Hub is the most convenient way to install applications in the workspaces.

## Alnoda Hub apps

To install application from Alnoda Hub use command `wrk install` following by the application name. For example, to install Postgres 
database in the workspace execute: 

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

You can also install a specific version of the application:

<div class="termy">
```
$ wrk install apache-airflow==2.5.2

✨ starting...
⚠️ Please DO NOT close this terminal window untill app is fully installed!
➡️ checking workspace compatibility...
➡️ checking app compatibility...
➡️ assigning port...
➡️ executing installation script...
✔️ app installed
➡️ setting startup configuration...
-------------------------------------------------------------
- ⚠️ application will start after workspace is restarted ⚠️  -
---       restart workspace with    'wrk kill'             ---
-------------------------------------------------------------
➡️ updating workspace UI...
➡️ adding workspace tags...
❗ Could not update workspace app history at alnoda.org: Not authenticated at alnoda.org
✍️ If app is not working try restarting terminal window or entire workspace
🚀 done
R E S T A R T    T E R M I N A L    N O W   (CTRL+D) !!!!!!!!
***********************************************
Airflow development installation with SQLite db, sequential executor and WEB UI. Use to develop and test locally Airflow DAGs.

1. WEB UI auth (user/pass): admin/admin

2. Airflow DAG folder: /home/abc/airflow/dags (place your dags here and refresh web ui)
***********************************************
```
</div>

!!! warning 
    Always review the results from executing `wrk install`. A workspace restart may be required after the application installation.
    You can restart workspace with the comand `wrk kill`

!!! note 
    It's important to restart your terminal after the installation process concludes. This step ensures the proper activation of the 
    environment, allowing for the smooth operation of the newly installed application.

!!! hint 
    Remember to log into Alnoda Hub from your workspace. This keeps track of your logged workspaces and installed applications, 
    significantly enhancing the reproducibility of workspace environments.

## Adding apps to Alnoda Hub

Should you require an application across multiple workspaces, think about adding it to Alnoda Hub. 

Applications in Alnoda Hub are merely setup and startup scripts, supplemented with metadata such as tags and usage hints. 
Take a look at applications in Alnoda Hub, examine their installation scripts, and see how straightforward it is to add 
applications to the Alnoda Hub.


## Alnoda Hub collections

With Alnoda Hub, you can install a bundle of applications using just one command. For instance, the following command installs the 
VSCode IDE, a file manager, a desktop environment, and a terminal workspace:

<div class="termy">
```
<font color="#5EA702">wrk</font> install bluxmit
```
</div>

This Alnoda Hub application - is just several `wrk install` commands 

```bash 
wrk install openvscode
wrk install kodexplorer
wrk install cloud-commander
wrk install zellij-ui
```

Create your own set of frequently used applications, save it as an application within Alnoda Hub, and install them in your 
new workspaces using a single command.
