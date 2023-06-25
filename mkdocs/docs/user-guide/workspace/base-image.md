# Base image 

Alnoda workspaces are based on the popular minimized Ubuntu image, which means that standard Linux Ubuntu commands are available 

| Command | Description | Example |
|---------|-------------|---------|
| sudo    | Allows a permitted user to execute a command as the superuser or another user. | `sudo apt-get update` |
| apt-get | The APT package handling utility (CLI), used for example to install or update software. | `apt-get install pkgname` |
| cd      | Changes the current directory. | `cd /home/username/Documents` |
| ls      | Lists all files and directories in the current directory. | `ls` |
| pwd     | Displays the path of the current directory. | `pwd` |
| touch   | Creates a new empty file. | `touch newfile.txt` |
| cp      | Copies files and directories. | `cp source destination` |
| mv      | Moves or renames files and directories. | `mv oldname newname` |
| rm      | Removes files or directories. | `rm filename` |
| cat     | Displays the content of a file. | `cat filename` |
| grep    | Searches for a specific pattern in a file. | `grep 'word' filename` |
| chmod   | Changes the permissions of a file or directory. | `chmod 755 filename` |
| chown   | Changes the ownership of a file or directory. | `chown username:group filename` |
| ps      | Shows the currently running processes. | `ps` |
| top     | Displays real-time system information including CPU usage, memory usage, and running processes. | `top` |
| df      | Displays disk usage. | `df` |
| du      | Estimates file and directory space usage. | `du` |
| ping    | Checks network connectivity. | `ping www.example.com` |

## User 

The workspace is initially set to the user 'abc', who belongs to the sudo group. 
However, you have the option to switch to the root user by using the command `sudo su root`.

## Project dir

The `/home/project` directory is designated as the default working directory where you can store code repositories, data files, artifacts, and so on. 
The alias `cd ~p` can be used to quickly navigate to this project folder.
 
## Processes   

Docker is typically used to run a single process within a container. However, workspaces have multiple processes and, for this reason, they leverage supervisord. 
Supervisord ensures that as soon as a workspace container is initiated, all the necessary persistent services also start running.

## Cron 

Cron, a time-based job scheduling system, can schedule jobs (commands or scripts) to run periodically at fixed times, dates, or intervals. 
It is commonly used to automate system maintenance or administration tasks, such as disk backups, system updates, checking and reporting, etc.

Cron is pre-configured in the workspace, and its daemon service automatically starts upon the starting of the workspace.

To schedule an execution of a task edit crontab file:

<div class="termy">
```
<font color="#5EA702">crontab</font> -e
```
</div>

```
Example of cron job definition:   
.---------------- minute (0 - 59)   
|  .------------- hour (0 - 23)
|  |  .---------- day of month (1 - 31)
|  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ...
|  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
|  |  |  |  |
*  *  *  *  *  command to be executed
```

For example to schedule a task that will every minute append username at the end of the text file `/home/project/my-username.txt` you would add to the 
crontab the following line: 

```
* * * * * echo $(whoami) >> /home/project/my-username.txt
```