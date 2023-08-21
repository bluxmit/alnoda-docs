# Alnoda App 

_"Applications"_ in the Alnoda Hub are merely shell scripts that will install and configure applications in the workspaces. The latter 
are built from the base images - the LTS version of Ubuntu, hence Alnoda Apps will be compatible with early all of the workspaces. 

Alnoda has deliberately chosen plain straight shell as a wehicle to install applications, without relying on popular tools such as Chef or Ansible. 
Basic shell makes it very clear what is going to be executed, allows to look through the script before installing and does not require to 
learn the tool that you might not be familiar with.   

!!! info 
    App script (for the given version) is immutable, it cannot be changed. This guarantees stability and removes the eed to review the installation script every time you need to install this version. 

## App page

Every App has its own page in Aloda Hub with short description, installation script, relevant links to the docs and code repository and optional notes. 

![app page gossa](./img/app-page-gossa.jpg)

## App Info 

Each App has name, description, tags, links to docs, repository and/or main website, install command (execute in the workspace terminal to install application), installation script, and optional notes, where author of the installation script can write remarks, such as default login credentials, how to get a secret, location of the configuration file, example how to use application in terminal etc.  

![app airflow](./img/app-airflow.jpg)

Every application has __installation script__ - _a sequence of shell commands that will usually perform such actions as downloading and installing binaries, cloning Git repositories, installing runtimes and virtual environments, building applications from source, downloading artifacts and making app configurations, such as setting environmental variables or creating configuration files_. 

![airflow install script](./img/airflow-install.jpg)

Applications that run as service will also have the startup command. This is a command that is used to start application every time the workspace is started (or restarted). Applications with UI will also have image for the workspace home tab. After app is installed, this tab will appear in the workspace UI, and serve as convenient shortcut to ope application

![airflow run script](./img/airflow-run-script.jpg)

Different applications with UI listen to varios ports. You don't need to care about it, the traffic will be automatically forwarded to one of the free workspace ports that were reserved for workspace applications and mapped to the host network.

## Versions

Alnoda apps have versions, that usually should match the version of the installed application itself. There can be differences though when several pplications are installed together, or new version is created to fix the bug in the installation script itself. 

!!! note
    Anyone can add versions to any Alnoda app, even if this app is not created by you.  

To add another version to the Alnoda app (created by you or anyone else) click button in the top right corner. You must have account and signed in to do this.  

![app version button](./img/app-version-btn.jpg)

## Workspace Compatibility


## App Compatibility