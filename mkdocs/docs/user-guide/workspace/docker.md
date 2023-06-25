# Docker

## Run workspace

Alnoda workspaces come in the form of Docker images that can be executed just like any other Docker container. 
Use the following command to run them:

```shell
docker run --name workspace-1 -d -p 8020-8040:8020-8040 --restart=always alnoda-workspace:latest
```

Once it's running, you can access the Workspace UI by navigating to [__http://localhost:8020__](http://localhost:8020) 
in your web browser.

## Other ports
Alnoda workspaces requires the availability of 20 ports, mapped internally to the range 8020-8040. If you need to designate 
a different range of ports, include an environmental variable, WRK_HOME_PORT, set equal to the first port in the new range. 
For example:

```shell
docker run --name workspace-2 -d -p 7020-7040:8020-8040 -e WRK_HOME_PORT=7020 --restart=always alnoda-workspace:latest
```

Now Workspace UI will be available on [__http://localhost:7020__](http://localhost:8020)

## Start, stop, restart 

You have the flexibility to manage workspaces just as you would with any Docker images and containers. This includes operations such as starting, stopping, and deleting.

To stop a workspace, use:
```shell
docker stop workspace-1
```

To start a workspace, use:
```shell
docker start workspace-1
```

!!! note 
    You also have the option to restart a workspace directly from within the workspace terminal using the `wrk kill` command.

!!! info 
    Every application initialized as a resilient service is designed to launch automatically whenever the workspace is rebooted.

## Save workspace 

Workspaces can be backed up by generating new images from current workspaces. It's not necessary to stop a workspace for this process, 
as backups can be made while the workspace is operational: 

```shell
docker commit workspace-1 workspace-1-backup-image:2023-05-01 
```

It is possible to start a new workspace using the backup:

```shell
docker run --name workspace-1 -d -p 8020-8040:8020-8040 --restart=always workspace-1-backup-image:2023-05-01
```

Saving a workspace backup as a file offers several benefits. It ensures the backup's security against unintended removal 
during purges of old Docker images. It also provides the flexibility to transfer the backup file to a cloud storage service 
like S3 or Google Drive. Additionally, it facilitates sharing of the backup file to another computer, allowing the workspace 
to be launched there.

Save workspace backup image to a file: 

```shell
docker save workspace-1-backup-image:2023-05-01 > workspace-1-backup-image-2023-05-01.tar
```

Load workspace image from the tar file: 

```shell
docker load < workspace-1-backup-image-2023-05-01.tar
```

!!! tip 
    Another even better approach is to utilize a private Docker registry as a repository for your workspace backups.

