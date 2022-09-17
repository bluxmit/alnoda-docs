# Kakoune - a better code editor 

## Intro 

In this example we will install [__Kakoune__](https://github.com/mawww/kakoune#22-installing) - a code editor that implements Vi’s 
"keystrokes as a text editing language" model.  

As it is also a modal editor, it is somewhat similar to the Vim editor (after which Kakoune was originally inspired).

## Install

The first thing is to update the package lists. Open workspace terminal and run  

<div class="termy">
```
$ sudo apt-get update

Fetched 339 kB in 2s (185 kB/s)
Reading package lists... Done
```
</div>

Now we can install Kakoune with Apt package manager 

<div class="termy">
```
$ sudo apt install -y kakoune

Preparing to unpack .../kakoune_2019.07.01-1build1_amd64.deb ...
Unpacking kakoune (2019.07.01-1build1) ...
Setting up kakoune (2019.07.01-1build1) ...
```
</div>

[__Kakoune__](https://github.com/mawww/kakoune#22-installing) was installed in the workspace.  

## Use

To open Kakoune code editor simply execute `kak` in the terminal

<div class="termy">
```
$ kak
```
</div>