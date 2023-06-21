
# Install packages with APT

The Advanced Package Tool, or APT, is a CLI utility for handling packages in Alnoda workspaces, which are based on Ubuntu. 
Debian packages can be installed in Alnoda workspace usin APT.

__Here is the general process to install packages using APT:__

- [x] First, update the package lists for upgrades and new package installations 

<div class="termy">
```bash
<font color="#5EA702">sudo apt</font> update 
```
</div> 

- [x] Next, use the install command followed by the name of the package you want to install. For example, to install a package 
named package_name, you would use:

<div class="termy">
```bash
<font color="#5EA702">sudo apt</font> install package_name 
```
</div> 

If you aren't sure what the package name is, you can search for it using the following command:

<div class="termy">
```bash
<font color="#5EA702">apt-cache</font> search keyword
```
</div> 

For example, let's install __mle__ - a flexible terminal-based editor:

<div class="termy">
```bash
$ <font color="#5EA702">sudo apt</font> install mle

Reading package lists... Done
Building dependency tree       
Reading state information... Done
.......
Setting up mle (1.4.3-1) ...
Processing triggers for libc-bin (2.31-0ubuntu9.9) ...
```
</div> 
