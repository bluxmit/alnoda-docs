# Nix packages

[__Nix__](https://nixos.org/) is a powerful package manager for Linux and other Unix-like systems. It has a number of unique features 
which make it different from other traditional package managers:

- [x] Atomic upgrades and rollbacks: Nix ensures that installing or upgrading one package can't break others.
- [x] Multi-user package management: Non-privileged users can securely install packages and each user is prevented from interfering with others.
- [x] Source-based and binary-based: Nix allows you to build packages from source to customize build-time parameters, 
but also supports binary installs for quicker deployment.

!!! info
    Nix is istalled by default in every Alnoda workspace. Check out [__Nix package search__](https://search.nixos.org/packages) 
    to find the package you need!

You can install Nix packages with the `nix-env -iA nixpkgs.` command followed by the package name, like so 

<div class="termy">
```
<font color="#5EA702">nix-env</font> -iA nixpkgs.vis
```
</div>

!!! warning 
    Nix is designed to be deterministic, which means that it builds packages from source to ensure that the build process 
    is repeatable and results in the exact same output every time. Sometimes installation of Nix package can take time.