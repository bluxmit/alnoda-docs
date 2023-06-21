# Install applications in workspaces

Alnoda workspaces are architected to be very flexible and easy to augment with new tools and services. The goal is to simplify 
and speed up workspace creation and setup.

## Alnoda Hub 

Most importantly, we maintain and expand Alnoda Hub - a growing repository of applications which you can install and configure in your 
workspace with a one-line terminal command. 

!!! note
    Alnoda Hub is by far the most straightforward, robust, and convenient way to quickly provision workspaces, install and configure more tools 
    and applications, allowing you to tailor workspaces quickly to meet the exact requirements of your projects.

While Alnoda Hub has a wide array of applications, it might not cover all your needs. For such cases, Alnoda workspaces offer 
features to simplify the installation of extra applications.

## Package managers

To facilitate this, we equip all workspaces with a variety of package and plugin managers by default. This includes:

- [x] apt
- [x] nix
- [x] asdf
- [x] pipx

## Nodejs

Workspaces have also nodeenv, allowing to benefit from vast collection of browser-based Node.js applications and install them into 
separate environments.

## Workspace features 

Workspaces operate in Docker containers, which are initially designed for a single process. Hence, they lack some Linux tools 
like `systemd` used for bootstrapping user space and managing system processes. Instead, workspaces use `supervisord` to keep all 
processes active upon startup. 

Alnoda abstracts `supervisord` complexities with tools like 'wrk' and 'Alnoda admin', enabling easy 
initiation of applications and services, and addition of application shortcuts to the workspace interface.

!!! tip 
    Get familiar with `wrk` commands and Alnoda Admin to understand how to initiate installed applications and services. 
    You will also learn to add application shortcuts to the workspace user interface.

## Other programming languages 

Alnoda aims to facilitate the expansion of workspaces using specific programming languages and their associated toolsets. 
For instance, it allows the use of utilities like Cargo, Rust's package manager. Cargo manages the download of Rust project 
dependencies and their compilation into an application. 

!!! tip
    Browse this documentation to learn how to compile and install applications in various languages such as Nodejs, Go, Rust, Python, 
    Ruby, PHP, Java, and others in the workspaces.