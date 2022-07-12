This basic tutorial demonstrates how to make your applications and services runing in the workspace, 
even if you close the terminal.  

Any application started in the terminal will run as long as your terminal session is alive. There are couple of simple 
method that you can apply to let your application run in the background.   

For the sake of demonstration let's create a simple shell script. Execute 

```
nano /home/project/myscript.sh
```

This opens nano text editor. Let's make this script write to a file current time every 2 second.  
Paste the following code in the editor window 

```
#!/bin/bash
while true
do  
    echo $(date +"%Y-%m-%d_%H-%M-%S")
	echo $(date +"%Y-%m-%d_%H-%M-%S") >> /home/project/time.txt
    sleep 2s
done
```

Hit Ctrl+x to save, and start the script 

```
sh /home/project/myscript.sh
```

You see that it also outputs the timestamp to the console. Interrupt the execution with Ctrl-c, and check the 
contents of the file 

```
cat /home/project/time.txt
```

Let's remove this file, and start again 

```
rm /home/project/time.txt
sh /home/project/myscript.sh
```

Now close the terminal, and open it again. You can check the file `/home/project/time.txt` and you will see that it has some timestamps, 
but no new timestamps appear. This is because we termminated execution when closed the terminal. But sometimes you need your scripts, 
services and applications to run in the background, even if you close the terminal, and even if you restart your computer. 

The next couple of methods will show how to do that. 

## &!

If you want any application or service runing after terminal session is closed, you can start service with **"&!"** at the end of 
the command.  

For example, to start the script from example above and keep it running after terminal is closed, execute  

```
sh /home/project/myscript.sh &!
```   

Close the terminal, and open it again. Check the latest timestamp, print the file with

```
cat /home/project/time.txt
```

wait 5 seconds, and print the file again. You can see that new timestamps keep appearing. 

This is a very simple way to start your application i the terminal, and let it running even if you close the terminal. 
When you want to stop it, you will need to find it among running processes, and kill it. 

```
ps -axf | grep /home/project/myscript.sh
```

the first number is PID, kill the process with the `kill <your-PID-number>` command, i.e. 

```
kill 154
```

*(your PID might be different)*


**Note:** if you restart the workspace, execution will be terminated too.  

Remove the output file 

```
rm /home/project/time.txt
```

## Tmux 

Tmux - is another even better way to let application running in the background.  

Tmux is a Linux application that allows multitasking in a terminal window. It stands for Terminal Multiplexing, and is based around sessions. 
Users can start a process, switch to a new one, detach from a running process, and reattach to a running process.

Create tmux session, let's call it "session-1" (you can give any name)

```
tmux new -t session-1
```

This opens new console widow. Here we can d same things that we could run in the main termianl. For example, show your user 

```
whoami
```

Now let's start our script in this tmux session terminal 

```
sh /home/project/myscript.sh
```

You see that the script is being executed, and the output is printed to the console. Let's close the terminal, and open the new one.  

In the new terminal let's check that out text file is constantly being updated by the script running somewhere in background 

```
cat /home/project/time.txt
```

wait few second and check again, you will see new timestamps appearing

Let's ist the tmux sessions. To do this execute command 

```
tmux list-sessions 
```

You see our session-1. Let's open terminal of this session

```
tmux attach -t session-1
```

UYou see that our has being running all the time, and even output was printed inside this session terminal. 

**Note:** if you restart the workspace, all tmux session will be lost.  