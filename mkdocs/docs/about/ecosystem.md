<p align="center">
  <img src="../img/ecosystem.svg" alt="" width="300">
</p>


# Alnoda Ecosystem

Alnoda ecosystem consists of tools, Docker images, and cloud services that enable convenient containerized development environments for 
various IT professionals ad projects. 

## Alnoda workspace 
__Alnoda workspace__ is a foundatio worksapce Docker image that is specifically designed to accommodate multiple services running within 
a single container. This Docker image is equipped with a user interface that allows seamless installation of new packages 
and applications. 

Moreover, Alnoda workspaces offer great flexibility by allowing users to install applications from the Alnoda Hub, 
to create a highly customizable environment. By means of an administrative interface, users can effortlessly personalize 
their workspaces and manage various settings. Furthermore, Alnoda workspaces effectively store and update important metadata 
related to workspace features and installed applications, ensuring a comprehensive and efficient development experience.

The foundation Alnoda workspace image is based on Ubuntu Linux and includes a wide range of commonly used applications such as 

- user interface for the workspace 
- browser-based terminal
- browser-based file manager

This image is Ubuntu Linux-based, having many widely used applications pre-installed CLI tools such as

- Git
- text editors: nano, vim, tilde 
- tools for managing packages and software dependencies: apt, nix, asdf 
- tools for interacting with servers and downloading files over the internet: curl, wget 
- tools for archiving and compressing files: tar, zip
- process monitor: htop
- disk usage analyzer: ncdu
- utility to multiplex several virtual consoles: tmux
- Z shell (zsh) - shell that offers a more user-friendly and interactive command-line experience. 

!!! info 
    __Alnoda workspace__ is the basis image for other Alnoda workspaces, which have all the features of Alnoda workspace.

## Alnoda Hub
Alnoda Hub is a cloud platform designed to register workspaces and applications that are compatible with Alnoda workspaces. 
It allows you to conveniently add frequently used applications to the Alnoda Hub, making them easily installable in any workspace 
with a single command.

With Alnoda Hub, you have the ability to create personalized collections of applications and store them for future use. 
These collections can be saved within the Alnoda Hub, ensuring easy access and allowing you to provision workspaces with 
the required functionality effortlessly.

Furthermore, when logged in from your workspaces, you can conveniently save a log containing information about all the installed 
applications. This log serves as a record of the applications installed in your workspaces, enabling easy reference.

## Aloda workspaces  
Growing collection of workspaces. Each workspace is constructed using the Alnoda workspace or other workspaces. Every individual 
workspace inherits all the features of the foundation Alnoda workspace, along with the combined features of all the workspaces 
from which it originates.

Alnoda manages a collection of workspaces in the [alnoda-workspaces](https://github.com/bluxmit/alnoda-workspaces) GitHub repository.  

Any workspace from any repository can be registered in the Alnoda Hub, which simplifies their discovery.

## Alnoda desktop 
The Alnoda desktop application provides comprehensive support for managing multiple workspaces efficiently. It offers the following key features:

- Workspace Management: the application allows to seamlessly switch between multiple workspaces, providing a convenient way to organize and access 
different development environments or projects.
- Workspace Saving, Backup, and Restoration: this ensures that important progress and configurations are preserved and can be reverted to if necessary.
- Workspace Synchronization: synchronize workspaces across different computers and servers. This makes workspaces truly portable. Having 
stopped workspace on one computer you can start it on the other one. 
- Cloud Server Workspace Deployment: start their workspaces on cloud servers directly from the Alnoda desktop application. This functionality 
provides the flexibility to utilize remote computing resources, enabling efficient development and resource utilization.

## Alnoda-wrk
Alnoda-wrk (wrk) is a ClI tool that helps with building new workspaces, and perform actions in the running workspaces:

- install application from Alnoda Hub 
- show list of applications
- add environmental variables or terminal aliases 
- start services
- sign in and sign out to Alnoda Hub
- restart workspace

## Alnoda Helm chart
Generic helm chart that can be used to launch any Alnoda-compatible workspace in a Kubernetes cluster. 

## Alnoda docs
Docs for Alnoda workspaces users and developers.

!!! warning
    These Alnoda features are in active development, and not publicly available yet: 1) Alnoda desktop app; 
    2) Alnoda Helm chart

