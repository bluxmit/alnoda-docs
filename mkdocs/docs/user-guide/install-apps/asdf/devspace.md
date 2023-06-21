# DevSpace

In this example we will istall [__DevSpace__](https://www.devspace.sh) - an open-source developer tool for Kubernetes that 
lets developers build, test, and debug applications directly inside Kubernetes. It essentially aims to automate the deployment 
process of applications in a Kubernetes environment.

!!! info 
    DevSpace can be installed in any workspace. We will use __Alnoda workspace v.1.1__ in this example.

Install devspace plugin :

<div class="termy">
```
<font color="#5EA702">asdf</font> plugin-add devspace
```
</div>

Show all installable versions:

<div class="termy">
```
<font color="#5EA702">asdf</font> list-all devspace
```
</div>

Install specific version:

<div class="termy">
```
<font color="#5EA702">asdf</font> install devspace latest
```
</div>

Set the latest devspace version globally:

<div class="termy">
```
<font color="#5EA702">asdf</font> global devspace latest
```
</div>

Now devspace commands are available:

<div class="termy">
```
$ devspace --version

devspace version 6.3.2
```
</div>


