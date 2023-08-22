# Install Apps

Application from the Alnoda Hub can be installed in your workspace, if the app is compatible with the workspace. 

!!! info 
    You do not need account in the Alnoda Hub to install applications

You can install apps added by you or other people. To install an app you need to execute a single command in the workspace terminal 


<div class="termy">
```
<font color="#5EA702">wrk</font> install [app-id]==[app-version]
```
</div>


For example to install Nginx execute  

![wrk install nginx](./img/nginx-install.png)

This application install command can be found in every application page in the Alnoda Hub

![install nginx](./img/nginx-install.jpg)

## Versions

You can install specific version of the application, if it is present. It is possible to install app without specifying a version. In this case the version which was added the last will be installed. For example  

<div class="termy">
```
<font color="#5EA702">wrk</font> install nginx
```
</div>

## Considerations

There are several things to consider when installig a application in your workspace 

- [x] Check out the stallation script if application is created by someone else. Most of the installation scripts are relatively small - betweenn 5 annd 20 commands, so it is not a hard task. 
- [x] Install a particular version of the application. Anyone can add a version to your app, hece specify the version explicitly, donn't rely on the lates added version.
- [x] Back up workspace before installing applicatio created by someone else or compatibility is doubtful. Backinng up a workspace is merely a single command, so it's worse it! 
- [x] It is not possible to uninstall an app inn the workspace. Better back up workspace before trying new application. 

Installation might not actually work! Alnoda applications are just a sequence of commannnds that download binaries, packages, repositories and then configure, build and install applications. But packages are moved, repositories rennamed, binary releases deleted. With time the chance of successful app installation dimisishes, and new version of the app might be required.