# Reports from notebooks 

Jupyter notebook - is a famous exploration and visualisation tool, which in turn makes it a good 
option to present the results or becoming a reporting solution.  

There are couple options how to create reports from notebooks.


## Nbconvert 

With [Nbconvert](https://nbconvert.readthedocs.io/en/latest/index.html) we can convert an .ipynb notebook 
to various static formats including HTML, PDF, LaTeX, Markdown.  

Workspace has a Static File Server, which serves HTML pages from folder `/home/static-server`. Let's convert 
Jupyter notebook to the HTML page in this folder

```
jupyter nbconvert --to html /home/examples/jupyter/magpye.ipynb --output /home/static-server/magpye
```

From the Quickstart page open Static File Server, and then open 'magpye.html'.  

![NBconvert HTML](img/nbconvert-html.png) 

If you want to hide code in the output, add `--no-input` flag

```
jupyter nbconvert --to html --no-input /home/examples/jupyter/magpye.ipynb --output /home/static-server/magpyeout
```

![NBconvert HTML no input](img/nbconvert-noinput-html.png) 

Nbconvert can convert to other formats too, such as PDF, 

```
jupyter nbconvert --to pdf /home/examples/jupyter/magpye.ipynb --output /home/project/magpye
```

From the Quickstart page open Filebrowser, go to folder '/home/project', preview and download pdf file 

![NBconvert PDF](img/nbconvert-pdf.gif) 

If you want to convert notebook to LaTeX, run

```
jupyter nbconvert --to latex /home/examples/jupyter/magpye.ipynb --output /home/project/magpyetex
```


## Voila

[Voilà](https://voila.readthedocs.io/en/stable/) allows you to convert a Jupyter Notebook into an interactive dashboard 
that allows you to share your work with others.   

Voila is up and running as a standalone application inside the workspace. Shortcut for Voila can be found on the Quickstart page.    

To serve notebok with Voila it is enough to move this notebook to the folder '/home/project/voila'.   

Voila can serve any notebook. Upon opening, notebook is executed. This is a differece with NBViewer that does not run 
notebooks.  

To demonstrate how Voila works, copy an example notebook to the served folder 

```
cp /home/examples/notebooks/basic-notebook.ipynb /home/project/voila/
```

Open Voila dashboard and check the notebook.  

![Voila](img/voila.png) 

Voila can also serve notebooks with interactive widgets, as well as notebook with Slides. 
Workspace has several examples of such interactive notebooks. Copy examples to the folder served

```
cp /home/examples/voila/* /home/project/voila/
```


## Datapane

[Datapane](https://github.com/datapane/datapane) is a Python library for building interactive reports for your end-users in seconds.  

Workspace has everything needed to get started with the Datapane. You can see how datapane works by following instructions and 
running cells in the tutorial notebook 'datapane.ipynb'.   

Save resulted reports in the folder '/home/static-server/', open Static Server from the Quickstart page, and explore the 
generated reports. 

![Datapane](img/datapane.png) 


## Cronicle

With [Cronicle](https://github.com/jhuckaby/Cronicle) we can easily schedule executions of shell commands and scripts. Cronicle 
has WEB UI, monitor of executions, collect logs and advanced features such as limiting resources for each execution.  

From the Quickstart page open Cronicle, (Cronicle user/pass: admin/admin), go to 'Schedule' and add new Event. Chose category 'General' 
and plugin 'Shell script'. Now we can configure the schedule, and provide any of the command to be executed.
