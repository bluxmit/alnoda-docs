<p align="center">
  <img src="../img/containers.svg" alt="" width="300">
</p>


# Containers

The core concept of containerization lies in encapsulating all the necessary dependencies, code, configurations and other artifacts required for a project 
within a self-contained unit known as a container. 

Docker has been widely adopted and successfully used to isolate development environments. Docker provides a lightweight 
and efficient solution for creating isolated and reproducible development environments.

## Existing solutions

The concept of utilizing Docker containers for isolated development environments has gained significant popularity, 
and there exists a wide range of solutions that facilitate this approach. 

!!! attention
    Despite Docker was widely adopted to isolate development environments in containers, existing solutions have significant limitations

The key limitations of the existing solutions:

- Docker introduces an additional layer of complexity to the development workflow. Developers need to learn Docker concepts, 
commands, and best practices, which may require upfront time investment and ongoing maintenance.

- Complexity of Configuration. Setting up the development environment with local IDE to work within Docker containers can involve 
configuring various files and settings, such as the Dockerfile, devcontainer.json, and extensions within the container. 
Managing these configurations and ensuring compatibility with specific project requirements may introduce additional complexity.

- Insufficient flexibility. Certain available choices are tailored to specific projects 
and lack extensibility. These options come with a predefined set of installed tools, making it challenging to add new tools 
as it often involves the complexity of building a new Docker image. 

- Lack of portability. Many existinng solutions often rely on specific tooling, configurations, or extensions that are tightly integrated with their respective environments. Moving these environments to different setups may require additional effort to ensure compatibility and proper functioning.

- Team Collaboration Challenges. Collaborating with team members who are not using specific tooling (for example, Visual Studio Code Remote) or who have different development environments can present challenges. Synchronizing configurations, ensuring compatibility, and maintaining consistency across the team may require additional coordination and effort.

## Alnoda features

Alnoda proposes a fresh approach to utilizing Docker containers for isolated development environments, prioritizing user-friendliness, flexibility, and expandability.

These features of Alnoda workspaces effectively address the common limitations found in other solutions:

- [x] __Docker abstraction.__ With Alnoda workspaces, you are abstracted from the intricacies and complexities of Docker. Setting up a sophisticated 
workspace with many running applications, packages and processes does not require in-depth knowledge of Docker.

- [x] __Self-contained.__ Alnoda workspaces are self-contained environments, encompassing all the necessary tools, applications, 
and packages you require. This makes it truly portable and eliminates the need to configure integrations with IDEs or terminals.

- [x] __Extendable__ It is very easy to add more applications, packages and frameworks even to the running workspace. All you need is to search in Alnoda Hub  
for the required tool, install with just onne command, and restart your workspace. 

- [x] __Browser-based.__ All applications in Alnoda workspaces are browser-based. No matter where you have deployed your workspace - you only need a web browser to work with it. 
This flexibility allows for seamless work across different devices and locations, making it ideal for remote work, collaboration, and on-the-go development. Fully browser-based workspaces 
facilitate seamless collaboration and sharing among team members, even when you are runninng workspace on your personal laptop!

!!! info
    Alnoda aims to deliver a convenient solution for project isolation through the utilization of Docker containers. Our primary objective is to establish workspace isolation in the most user-friendly manner possible.







