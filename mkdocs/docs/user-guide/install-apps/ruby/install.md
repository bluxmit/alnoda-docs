# Ruby applications 

You can install Ruby applications in the Alnoda workpspaces utilizing `gem` -  a package manager for the Ruby programming language 
that provides a standard format for distributing Ruby programs and libraries. It is included with Ruby, and it is analogous to pip 
in Python or npm in Node.js.

!!! warning 
    Ruby is not installed in the Alnoda workspaces by default. To install Ruby run `wrk install ruby`. Restart 
    terminal after installation is done. 

Before installing Ruby applications you need to install Ruby in the workspace:

<div class="termy">
```
<font color="#5EA702">wrk</font> install ruby
```
</div>

Please restart workspace terminal now!  

Having installed Ruby in the workspace, you can install Ruby applications with `gem`. For example let's install gem install Jekyll - 
a static site generator that's perfect for personal projects, blogs, or other websites that don't require a database.

<div class="termy">
```
<font color="#5EA702">gem</font> install jekyll -v 4.3.2
```
</div>

You can now use Jekyll

<div class="termy">
```
<font color="#5EA702">jekyll</font> -help
```
</div>


## Alnoda Hub 

If you are planning to register Ruby application in the Alnoda Hub, you need to start installation script with 
the command that installs Rybu and __set environmental variables__: 

```bash
wrk install ruby
export PATH="$PATH:/home/abc/.rbenv/bin:/home/abc/.rbenv/shims/" 
```
