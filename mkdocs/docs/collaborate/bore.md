# Bore - expose your local application to the internet

[__Bore__](https://github.com/ekzhang/bore) - is a modern, simple TCP tunnel in Rust that exposes local ports to a remote server, 
bypassing standard NAT connection firewalls. 

!!! note
    With a single terminal command you can share any workspace tool with your friend. 
    And your friend does not need to install any software. 

!!! attention
    Bore can be installed in any workspace. We will use __Codeserver workspace v.4.0__ for this example. 


## Install 

In order to install Bore simply copy the following code snippet and execute it in the workspace terminal

<div class="termy">
```
cd /tmp && wget https://github.com/ekzhang/bore/releases/download/v0.4.0/bore-v0.4.0-x86_64-unknown-linux-musl.tar.gz \
&& tar -xf bore-v0.4.0-x86_64-unknown-linux-musl.tar.gz \
&& chmod +x /tmp/bore \
&& mv /tmp/bore /home/abc/.local/bin/ \
&& rm /tmp/bore-v0.4.0-x86_64-unknown-linux-musl.tar.gz 
```
</div>


## Use

As soo as you have Bore installed, you can use it to publish any of your workspace applications on Internet.  

For example, in order to share workspace terminal, execute

<div class="termy">
```
bore local 8022 --to bore.pub 
```
</div>