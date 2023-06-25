# JupyterLite

In this example we will set up [__JupyterLite__](https://jupyterlite.readthedocs.io/en/latest/#build-your-own-jupyterlite) - 
a JupyterLab distribution that runs entirely in the browser built from the ground-up using JupyterLab components and extensions.  

![jupyterlite](img/jupyterlite.jpg)

!!! info
    JupyterLite is an entirely in-browser application and needs only to be served via static WEB server.  

## Preparation

Install [jupyterlite](https://pypi.org/project/jupyterlite/) which is used to generate static Jupyterlite website:  

<div class="termy">
```
$ pipx install jupyterlite --include-deps

installed package jupyterlite 0.1.0, installed using Python 3.8.10
  These apps are now globally available
    - doit
    - jupyter
    - jupyter-lite
    - jupyter-migrate
    - jupyter-piplite
    - jupyter-troubleshoot
    - pkginfo
done! ✨ 🌟 ✨
```
</div>

## Create

Now we can generate static website, and output the result into the folder `/home/abc/apps/jupyterlite`:

<div class="termy">
```
<font color="#5EA702">jupyter</font> lite build --output-dir /home/abc/apps/jupyterlite
```
</div>

Serve jupyterlite with the default workspace static server 

<div class="termy">
```
<font color="#5EA702">cd</font> /home/abc/apps/jupyterlite; <font color="#5EA702">python</font> -m http.server 8026
```
</div>

## Permanent service 

The serving of Jupyterlite will terminate as soon as you close the terminal session window. To make it permanent: 

- [x] Open workspace Admin and select "Workspace settings".
- [x] In the workspace settings, go to "Apps & Services".
- [x] Choose the "START NEW" option from the picklist.
- [x] As command provide the following;

```bash
cd /home/abc/apps/jupyterlite; python -m http.server 8035
```

!!! warning 
    This example relies on port 8035 being available within your workspace. To verify the availability of this port, 
    please consult the 'About' tab within your workspace's UI.

- [x] Save the service. 
- [x] Restart the workspace.

## Update UI

Let's add a card for JupyterLite on the Home page for quick access. UI tab needs an image, choose the one and upload using Filebrowser.  

- [X] Open workspace UI, navigate to "Admin" tab and open "Workspace settings". Then go to "Interface" tab and select "CREATE NEW" from the picklist.  
- [X] Give it any title, and any description
- [X] Choose image you have uploaded  
- [X] Enter port `8035` - the port of the static web server (Serve)
- [X] Enter path `jupyterlite/lab` 

Now we have a shortcut tab on the "Home" page to quickly onep JupyterLab 

![jupyterlite-home](img/jupyterlite-home.jpg) 


## Result

We have generated webpage with JupyterLite and serve it with Serve (static web server). We have created JupyterLite tab on the 
workspace UI.