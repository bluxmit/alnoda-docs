# Dockerfile 

Build new workspaces easily using a Dockerfile. Start from the base A[__Alnoda workspace__](https://hub.docker.com/r/alnoda/alnoda-workspace) or any derived Alnoda workspaces 
to create your customized workspace. 

!!! hint 
    __wrk tool__ can be used in Dockerfile 


## Install apps 

In Dockerfiles, you can utilize `wrk install` to install applications from Alnoda Hub. For instance:

```docker 
FROM alnoda/alnnoda-workspace:1.1

RUN wrk install openvscode
RUN wrk install cronicle==0.9.10 admin
RUN wrk install serve==14.0.1 
RUN wrk install terraform==1.2.8 
RUN wrk install terrascan==1.15.2
RUN wrk install tfsec==1.27.5
RUN wrk install tflint==0.39.3
RUN wrk install terraform-docs==0.15.0
RUN wrk install inframap==0.6.7
RUN wrk install blast-radius==0.1.23
RUN wrk install rover-terraform-visualizer==0.3.3
```

## wrk build 

__wrk__ CLI tool includes commad __build__, which provides a way to configure workspaces using _workspace.yaml_ configuration file:   

- [x] Set workspace metadata: name, colors, fonts, icons, links
- [x] Add workspace UI shortcuts
- [x] Start applications and services 

To use __wrk build__ create _workspace.yaml_ configuration file:

```yaml
---
# Meta (mandatory) 
name: Extended workspace
doc_url: https://extended-workspace/
author: myself
version: 1.0.1
description: |
  # Extended workspace
  General-purpose portable containerized browser-based environment for code development and execution.  
  Includes code editor, terminal, file browser, Git manager and visual jobs scheduler.

tags: task-scheduler, static-file-server

# UI icons (optional)
logo: extended-workspace-white.svg
favicon: extended-workspace.svg

# Homepage UI appearance (optional)
styles:
  colors:
    light:
      primary: "#2A2D2E"
      accent: "#E77260"
    dark:
      primary: "#3C3C3C"
      accent: "#E77260"
      background: "#1E1E1E"
      title: "#9CDCFE"
      text: "#9CDCFE"
      code_text: "#EAB676"
      code_background: "#3C3C3C"
  common_colors:
    nav: "#eab676"

# Add shortcuts to the workspace UI (optional)
pages:
  home:
    - name: Static file server
      port: 8028 
      path: /
      title: Static File Server
      description: "Serve any static websites like a breeze"
      image: static-file-server.png
  admin:
    - name: Cronicle
      port: 8029 
      path: /
      title: Cronicle
      description: "Schedule jobs, manage schedules, observe and monitor executions (user/pass - admin/admin)"
      image: cronicle.jpg

# Start applications and services (optional)
start:
  - name: Static file server
    folder: $STATIC_FILESERVER_DIR
    cmd: . env/bin/activate; serve -p 8028 /home/static-server
  - name: Cronicle
    folder: $CRONICLE_DIR
    cmd: rm ./logs/cronicled.pid || true; . env/bin/activate; $CRONICLE_DIR/bin/control.sh setup; $CRONICLE_DIR/bin/control.sh start 
```

In Dockerfile COPY into the image a folder with _workspace.yaml_ together with the assets (images and icons) and run __wrk build__:

```docker
COPY --chown=abc:abc workspace /tmp/workspace
RUN wrk build /tmp/workspace  
RUN rm -rf /tmp/workspace
```
