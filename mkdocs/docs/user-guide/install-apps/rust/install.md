# Rust applications 

You can install Rust applications in the Alnoda workspaces using Cargo, the Rust package manager. But before Rust 
should be installed. 

!!! note 
    Rust and cargo are not installed in aloda workspaces by default. To install Rust ad Cargo in any Alnoda workspace run `wrk install rust`

## Crate registry

After you installed Rust in your workspace you can install any application from the [__Crate registry__](https://crates.io/). 
For example install [__halp__](https://crates.io/crates/halp) - a CLI tool to get help with CLI tools: 

<div class="termy">
```
$ cargo install halp 
...
<font color="#93DA41">Installing</font> /home/abc/.cargo/bin/halp
  <font color="#93DA41">Installing</font> /home/abc/.cargo/bin/halp-completions
  <font color="#93DA41">Installing</font> /home/abc/.cargo/bin/halp-mangen
  <font color="#93DA41">Installing</font> /home/abc/.cargo/bin/halp-test
   <font color="#93DA41">Installed</font> package `halp v0.1.7` (executables `halp`, `halp-completions`, `halp-mangen`, `halp-test`)
```
</div>

Now when halp is globally installed let's utilize it to get info about `cargo` command 

<div class="termy">
```
<font color="#5EA702">halp</font> plz cargo
```
</div>

## From source

With `cargo` we can build and install rust applications from source. Let's install `ripgrep`, a line-oriented 
search tool that recursively searches your current directory for a regex pattern.

Clone Git repository and navigate into it:

<div class="termy">
```
<font color="#5EA702">git</font> clone https://github.com/BurntSushi/ripgrep.git
<font color="#5EA702">cd</font> ripgrep
```
</div>

Compile the program and install it using `cargo`:

<div class="termy">
```
<font color="#5EA702">cargo</font> build --release
```
</div>

This command will create an optimized executable in the target/release directory. You can then move it into a directory that's 
in the workspace's PATH. For example:

<div class="termy">
```
<font color="#5EA702">mv</font> target/release/rg /home/abc/bin/
```
</div>

Ripgrep is globally installed, and you can use it with `rg` command:

<div class="termy">
```
<font color="#5EA702">rg</font> -help
```
</div>

## Alnoda Hub 

If you are planning to register Rust application in the Alnoda Hub, you need to start installation script with 
the command that installs Rust and __set environmental variables__: 

```bash
wrk install rust
export PATH="$PATH:/home/abc/.cargo/bin/"
```