# Install Go applications 

You can install Go(lang) applications from the source code with the command `go install`. With `go` being a tool for managing Go source code, 
`go install` command is used to compile and install packages and dependencies.

To install Go applications you'll need to make sure you have Go installed in the workspace. You can do this by running `go version` 
in your terminal. If Go is installed, it will return the version, if not, you'll need to install Go first. 

!!! note 
    Go is not installed by default in Alnoda workspaces. You can install Go in awny Alnoda with the command `wrk install go`

The first thing to do is to install Go in the workspace: 

<div class="termy">
```
<font color="#5EA702">wrk</font> istall go 
```
</div>

!!! warning 
    After installing Go please reload terminal

Now you can install any go application with the command `go install`. Let's install [__hey__](https://github.com/rakyll/hey) 
- HTTP load generator:

<div class="termy">
```
$ go install github.com/rakyll/hey@latest

go: downloading github.com/rakyll/hey v0.1.4
go: downloading golang.org/x/net v0.0.0-20181017193950-04a2e542c03f
go: downloading golang.org/x/text v0.3.0
```
</div>

You can now use hey to send some load to a web application. For example, if you want to send 1000 requests to `http://localhost:8080`, 
you can do so as follows:

<div class="termy">
```
<font color="#5EA702">hey</font> -n 1000 http://localhost:8080
```
</div>

## Alnoda Hub 

If you are planning to register Go application in the Alnoda Hub, you need to start installation script with 
the command that installs Go and __set environmental variables__: 

```bash
wrk install go
export PATH="$PATH:/home/abc/go/bin" 
```
