# Images 

Alnoda workspaces are Docker images, enabling you to perform all the typical Docker image operations such as building, committing, pushing, and pulling. 
You can also build new workspaces from existing ones, enhancing their functionality.


## Base image

[__Alnoda workspace__](https://hub.docker.com/r/alnoda/alnoda-workspace) acts as a _base image_ for other Alnoda workspaces. It contains essential components 
such as workspace UI, terminal, file browser, _wrk CLI tool_, and _Alnoda admin_. New workspaces can be built directly from the base image, or from other Alnoda workspaces 
that derive from it.

## Why building workspaces

There are several reasons: 

- [x] Preserve valuable workspaces by creating new images as backups.
- [x] Establish a foundation image for all your projects, encompassing secrets, environmental variables, and GitHub credentials.
- [x] Construct team workspaces with a wide array of tools and configurations.


## Commit to image 

The easiest method to generate a new workspace image is by committing a running or stopped workspace into a fresh image. This image will encapsulate all the 
installed applications and packages, user configurations,  as well as cloned repositories and uploaded artifacts.

For example, if your workspace called _my-workspace_ you can create new workspace image with a sinngle command: 

```shell
docker commit my-workspace my-new-workspace:2023-05-01 
```

Of course, instead of _my-new-workspace:2023-05-01_ you can use any name and tag.
