# n³

In this example we will install [__nnn (n³)__](http://harelba.github.io/q/) - a full-featured terminal file manager. 
It's tiny, nearly 0-config and incredibly fast. It is designed to be unobtrusive with smart workflows to match the trains of thought.   

[__nnn__](http://harelba.github.io/q/) is a terminal-based application without a graphical user interface.  

!!! info 
    [__nnn__](http://harelba.github.io/q/) can be installed in any workspace. We will use __Codeserver workspace v.5.0__ for this example. 

## Install

We can download nnn from the [__nnn releases page__](https://github.com/jarun/nnn/releases). Sometimes it is not obvious which 
binary to dowload. The workspace is based on Ubuntu image, hence Debian application binary packages are the right choice.  

Open workspace terminal, and execute

<div class="termy">
```
$ cd /tmp 
08:01:30 with <font color="#FDEB61">abc</font> in <font color="#37E6E8">/tmp</font> <font color="#98E242">➜</font>

$ wget https://github.com/jarun/nnn/releases/download/v4.6/nnn-static-4.6.x86_64.tar.gz

nnn-static-4.6.x86_64.tar.gz.1      100%[=================================>] 626.85K   505KB/s    in 1.2s    

2022-09-06 18:15:26 (505 KB/s) - ‘nnn-static-4.6.x86_64.tar.gz.1’ saved [641894/641894]
```
</div>

Extract the file from tar file 

<div class="termy">
```
$ tar -xzf nnn-static-4.6.x86_64.tar.gz
08:01:31 with <font color="#FDEB61">abc</font> in <font color="#37E6E8">/tmp</font> <font color="#98E242">➜</font>
```
</div>

We have extracted a file `nnn-static`. Let's make it executable 

<div class="termy">
```
$ chmod +x nnn-static
08:01:31 with <font color="#FDEB61">abc</font> in <font color="#37E6E8">/tmp</font> <font color="#98E242">➜</font>
```
</div>

Now we can move the binary to the folder, which is included in the $PATH environmental variable. It can be 
either `/home/abc/bin/` or `/home/abc/.local/bin/`

<div class="termy">
```
$ mv nnn-static /home/abc/bin/nnn
08:01:32 with <font color="#FDEB61">abc</font> in <font color="#37E6E8">/tmp</font> <font color="#98E242">➜</font>
```
</div>

Great! We can now start [__nnn__](http://harelba.github.io/q/) by executing `nnn -dHe` in the terminal.  

We can also install all the [__nnn plugins__](https://github.com/jarun/nnn/tree/master/plugins#installation) 

<div class="termy">
```
$ curl -Ls https://raw.githubusercontent.com/jarun/nnn/master/plugins/getplugs | sh

...
'./autojump' -> '../../plugins/autojump'
'./suedit' -> '../../plugins/suedit'
'./kdeconnect' -> '../../plugins/kdeconnect'
'./gpgd' -> '../../plugins/gpgd'
```
</div>
