
In this example we will install [__q__](http://harelba.github.io/q/) which allows to run SQL directly on CSV or TSV files.

q's purpose is to bring SQL expressive power to the Linux command line by providing easy access to text as actual data, 
and allowing direct access to multi-file sqlite3 databases. [__q__](http://harelba.github.io/q/) is a terminal-based application without a graphical user interface.   

!!! info 
    [__q__](http://harelba.github.io/q/) can be installed in any workspace. We will use __Codeserver workspace v.5.0__ in this example. 

## Install 

The first thing to do is to download the [__q__](http://harelba.github.io/q/#installation) binary package. Open workspace 
terminal and execute the following commands

<div class="termy">
```
$ cd /tmp 
08:01:30 with <font color="#FDEB61">abc</font> in <font color="#37E6E8">/tmp</font> <font color="#98E242">➜</font>

$ wget https://github.com/harelba/q/releases/download/v3.1.6/q-text-as-data-3.1.6-1.x86_64.deb 

q-text-as-data-3.1.6-1.x86_64.deb   100%[==================================>]  26.36M  1.72MB/s    in 9.2s    

2022-09-05 08:03:32 (2.87 MB/s) - ‘q-text-as-data-3.1.6-1.x86_64.deb’ saved [27641912/27641912]
```
</div>

Now we can install q

<div class="termy">
```
$ sudo dpkg -i q-text-as-data-3.1.6-1.x86_64.deb

Selecting previously unselected package q-text-as-data.
(Reading database ... 35238 files and directories currently installed.)
Preparing to unpack q-text-as-data-3.1.6-1.x86_64.deb ...
Unpacking q-text-as-data (3.1.6) ...
Setting up q-text-as-data (3.1.6) ...
```
</div>

You can check if __q__ is installed 

<div class="termy">
```
$ q 

q version 3.1.6
Python: 3.8.11 (default, Jul 24 2021, 23:08:48) // [Clang 12.0.1 ]
Copyright (C) 2012-2021 Harel Ben-Attia (harelba@gmail.com, @harelba on twitter)
http://harelba.github.io/q/

Must provide at least one query in the command line, or through a file with the -q parameter
```
</div>

## Use 

Let's create a dummy .csv file, and try querying it with [__q__](http://harelba.github.io/q/)

<div class="termy">
```
$ seq 1 1000000 > /home/project/myfile.csv
$ tail -n 3 /home/project/myfile.csv 

999998
999999
1000000
```
</div>

We have printed last 3 rows, and see that the .csv file is generated.  

Let's query it now with [__q__](http://harelba.github.io/q/) 

<div class="termy">
```
$ cd /home/project
08:01:33 with <font color="#FDEB61">abc</font> in <font color="#37E6E8">~p</font> <font color="#98E242">➜</font>

$ q "select sum(c1),count(*) from myfile.csv where c1 % 3 = 0"

166666833333 333333
```
</div>

Check out more examples on the [q documentation website](http://harelba.github.io/q/#getting-started-examples).  
