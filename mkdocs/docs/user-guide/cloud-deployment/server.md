# Cloud Server

Alnoda workspaces can be easily deployed in the cloud, with the simplest approach being the launch of workspaces as Docker containers.

When starting workspace on a server it is necessary to set a container environmetal variable `WRK_HOST` equal to the IP or the host name of the server. 
You can set this variable in the docker run command passing an argumentt `-e WRK_HOST="<ip-of-your-remote-server>"`.  

For example, if the IP of your server is _204.35.20.100_ you will start workspace on a server with a following command: 

```shell 
docker run --name space-1 -d -p 8020-8040:8020-8040 --restart=always -e WRK_HOST=204.35.20.100 alnoda/alnoda-workspace
```

!!! note 
    Please make sure that ports from the range 8020-8040 are not blocked by the firewall.

Ope browser on _<ip-of-your-remote-server>:8020_

However, when running on a cloud server with a public IP and accessing the workspace over the internet, it becomes necessary to establish a secure and 
encrypted connection with at least some authentication. You can do this using docker-compose. We have a companion repository with docker-compose file 
and instructions.

## HTTPS and authentication

To launch an Alnoda workspace on a cloud server with basic authentication over HTTPS using a self-signed certificate, follow these steps:

Ensure that the server has Docker and Docker Compose installed.

Verify that ports 8020 to 8040 are not blocked by the firewall. For instance, on Ubuntu/Debian, you can run the following command:

```shell
ufw allow 8020:8040/tcp
```

Clone the repository:

```shell
git clone https://github.com/bluxmit/wrk-compose.git
cd wrk-compose
```

Set the environmental variable WRK_HOST to the public server IP that allows access over the internet. For example:

```shell
export WRK_HOST=34.194.12
```

Start the workspace:

```shell
cd basic-auth-https
docker-compose up -d
```

Now you can open your browser and visit https://[WRK_HOST]:8020 to access the Alnoda workspace securely.


## Workspace selection 

By default, the latest version of the base Alnoda workspace will be launched.

If you wish to start another workspace, you can do so by setting the environmental variable WRK_IMAGE. For example:

```shell
export WRK_IMAGE='alnoda/codeserver-workspace:5.0'
```

This allows you to specify a different workspace image, such as _alnoda/codeserver-workspace:5.0_, to be used when starting the workspace.


## Authentication

The default authentication credentials are as follows:

Username: __admin__     
Password: __admin__

When you wish to create a new login for the workspace use _htpasswd_. 

If you don't know how to install _htpasswd_ in your system or on the server, you can install it in any of the Alnoda workspaces using the following command:

```shell
sudo apt-get install apache2-utils -y
```

Generate a new user:password pair:

```shell
echo $(htpasswd -nB <username>) | sed -e s/\\$/\\$\\$/g
```

Replace __<username>__ with the desired username. You will be prompted to enter a password, and htpasswd will generate the corresponding credentials. 
For example: __someuser:$$2y$$05$$t2MSJSPp2V9HdLWYq9z.UeYFz2R3un9ZuiBitSjeiN3Osz6fGNZ7u__.

Replace the credentials in the respective docker-compose YAML file, locate the label of the traefik service  

`traefik.http.middlewares.basic-auth.basicauth.users=admin:$$2y$$05$$eub6CV.CwUYCCQjNBvSf5uZnzdRmVwGZ/ncxecb9O7WxCR8aLuM3K` 

and replace __admin:$$2y$$05$$eub6CV.CwUYCCQjNBvSf5uZnzdRmVwGZ/ncxecb9O7WxCR8aLuM3K __ with the generated credentials.


## HTTP

!!! warning
    Using HTTP to access workspaces on a cloud server over public IP lacks the necessary security measures as it is not encrypted like HTTPS. This approach should be avoided unless you are operating within a secure internal network.

To start an Alnoda workspace on a cloud server with basic authentication over HTTP, you can utilize a separate docker-compose file:

```shell
cd basic-auth-http
docker-compose up -d
```
