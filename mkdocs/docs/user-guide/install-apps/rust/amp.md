# Amp 

In this example we will install [__amp__](https://github.com/jmacdonald/amp) - a complete text editor for your terminal.  

First thing is to install Rust and Cargo in the workspace: 

<div class="termy">
```
<font color="#5EA702">wrk</font> install rust
```
</div>

!!! warning
    After installation of Rust restart your terminal 

Install `libxcb1-dev`, a package required for building amp

<div class="termy">
```
<font color="#5EA702">sudo apt-get</font> install libxcb1-dev -y
```
</div>

Install amp with cargo:

<div class="termy">
```
<font color="#5EA702">cargo</font> install amp --version 0.6.2
```
</div>

Amp is installed. Open amp editor 

<div class="termy">
```
<font color="#5EA702">amp</font>
```
</div>

