# Calibre-Web - wseb app for browsing, reading and downloading eBooks

## Intro

In this example we are going to add [__Calibre-Web__](https://github.com/janeczku/calibre-web) - a web app providing a clean interface for browsing, reading and downloading eBooks using a 
valid [__Calibre__](https://calibre-ebook.com/) database.    



!!! attention
    Calibre-Web can be installed in any workspace. We will use __Theia workspace v.4.0__ in this example.  

!!! note
    Calibre-Web is a python package. We will install it in an isolated environment, start it as a permanent workspace application, 
    and create Calibre-Web shortcut in the workspace UI Home page.   

## Install 

[__Calibre-Web__](https://github.com/janeczku/calibre-web) is a python package. It can be installed with either __pip__ 
or [__pipx__](https://github.com/pypa/pipx). Both are present in every workspace.    

To install Label Studio open workspace terminal and execute 
<div class="termy">
```bash
$ pipx install calibreweb

  installed package calibreweb 0.6.19, installed using Python 3.8.10
  These apps are now globally available
    - cps
done! ✨ 🌟 ✨
```
</div>