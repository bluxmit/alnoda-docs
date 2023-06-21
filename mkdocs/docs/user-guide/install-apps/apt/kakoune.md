# Kakoune 

In the following demonstration, we'll be setting up [__Kakoune__](https://github.com/mawww/kakoune#22-installing), a code editor 
that utilizes Vi's design of using "keystrokes as a text editing language". 

Being a modal editor, it bears certain similarities to Vim (which initially inspired Kakoune's creation).

## Install

The first thing is to update the package lists. Open workspace terminal and run  

<div class="termy">
```
$ sudo apt update

Fetched 339 kB in 2s (185 kB/s)
Reading package lists... Done
```
</div>

Now we can install Kakoune with APT

<div class="termy">
```
$ sudo apt install -y kakoune

Preparing to unpack .../kakoune_2019.07.01-1build1_amd64.deb ...
Unpacking kakoune (2019.07.01-1build1) ...
Setting up kakoune (2019.07.01-1build1) ...
```
</div>

[__Kakoune__](https://github.com/mawww/kakoune#22-installing) is installed in the workspace.  

## Use

To open Kakoune code editor simply execute `kak` in the terminal

<div class="termy">
```
$ kak
```
</div>