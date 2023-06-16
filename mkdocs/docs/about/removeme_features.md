<p align="center">
  <img src="../img/cloud-computing.svg" alt="" width="400">
</p>

# Alnoda features

Alnoda proposes a fresh approach to utilizing Docker containers for isolated development environments, prioritizing user-friendliness, flexibility, and expandability.

These features of Alnoda workspaces effectively address the common limitations found in other solutions:

- [x] __Alnoda Docker image.__ Alnoda workspaces are built from a special Docker image designed to support multiple services runninng 
within a single container. Alnoda image is equipped with a user interface, enabling users to install new packages and applications 
seamlessly. Additionally, Alnoda workspaces offer the flexibility to add apps from Alnoda Hub, making the environment highly 
customizable. With an admin interface, users can easily personalize their workspace and manage various settings. Alnoda workspaces 
also store and update essential metadata regarding workspace features and installed applications, ensuring a comprehensive 
and efficient development experience.

- [x] __Alnoda Hub.__ [Alnoda Hub](https://alnoda.org) serves as a centralized repository for reusable scripts designed to install applications, 
packages, and dependencies within workspaces. By adding an installation script to Alnoda Hub, you can effortlessly install 
the required applications in any Alnoda workspace. Furthermore, you can create bootstrap scripts to provision an entire 
workspace with a single command, streamlining the setup process. Collaboration is encouraged through the sharing and reuse 
of scripts created by others. By signing in from your workspace to Alnoda Hub, you can conveniently log all the applications 
you have installed across your workspaces, ensuring seamless tracking and management.

- [x] __Browser-based.__ All applications in Alnoda workspaces are browser-based. No matter where you have deployed your workspace - you only need a web browser to work with it. 
This flexibility allows for seamless work across different devices and locations, making it ideal for remote work, collaboration, and on-the-go development. Fully browser-based workspaces 
facilitate seamless collaboration and sharing among team members, even when you are runninng workspace on your personal laptop!

- [x] __Self-contained.__ Alnoda workspaces are self-contained environments, encompassing all the necessary tools, applications, 
and packages you require. This makes it truly portable and eliminates the need to configure integrations with IDEs or terminals. 
You only need Docker to run alnoda workspace, and browser to use workspace.

!!! info
    Alnoda aims to deliver a convenient solution for project isolation through the utilization of Docker containers. Our primary objective is to establish workspace isolation in the most user-friendly manner possible.

