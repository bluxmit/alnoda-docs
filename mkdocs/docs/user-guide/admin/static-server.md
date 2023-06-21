# Static web server 

In this example we are going to add a very basic static web server to the workspace. Static file server is a very useful feature -
it will allow you to view HTML pages such as static websites (Hugo, MkDocs, Jekyll), HTML 
reports (great expectations) or use browser-based applications embed in the HTML websites that you download to the workspace.

To launch static serv er we don't actually need to install anythin. We will simply start 
python's [__http.server__](https://docs.python.org/3/library/http.server.html), which is already present in the workspace.   

!!! info
    [__http.server__](https://docs.python.org/3/library/http.server.html) is already installed in every workspace. We will use __Codeserver workspace v.4.0__ in this example.  

Start static http server: 

<div class="termy">
```bash
$ python -m http.server 8026'

Serving HTTP on 0.0.0.0 port 8026 (http://0.0.0.0:8026/) ...
```
</div>

Now you can open file server from the "My apps" tab - "My app on port 8026" 


## Add workspace service 

By setting up an application as a persistent workspace service, it will automatically launch whenever the workspace is started.

For example, let's initiate the http.server to run as a persistent service:

- [X] Open "Admin" tab oo the workspace UI and avigate to "Workspace Settings" 
- [X] Go to the tab "Apps & Services"
- [X] Select "START NEW" from the picklist 
- [X] Enter the following command 

```sh
cd /home; python -m http.server 8032
```

- [X] Give it any name you want 
- [X] Click "Save"

![http-start](img/http-server-start.jpg)

Restart workspace to apply changes.


## Create UI tab

Now let's create tab for the http.server on the "Homes" page  

- [X] Go to the "Interface" tab of the workspace settings and select "CREATE NEW" from the picklist.   
- [X] Give it any title and description. 
- [X] In the field "Port" enter port 8032 
- [X] In the file picker find your image.   
- [X] Leave field "path" blank and click "Create"

![http-ui](img/http-ui.jpg)

Now we have http.server tab on the Home page 

![http-home](img/http-home.jpg)