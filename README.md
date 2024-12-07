# Monutchee OS (MNCos) Project template

> [!WARNING]  
> This repo is still in construction.

# Introduction

This is a project template for building yocto on xilinx ZYNQ devices.

# Prerequisites

```bash
# Ubuntu 22.04
sudo apt install gawk wget git diffstat unzip texinfo gcc build-essential chrpath socat cpio python3 python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 python3-subunit zstd liblz4-tool file locales libacl1 libtinfo5 repo 

# Ubuntu 24.04
# Change libtinfo5 to libtinfo6

sudo locale-gen en_US.UTF-8
```

# Initialze you project

```bash
mkdir <your folder name>
cd <your folder name>
# Fetch the manifest and checkout the target release version
repo init -u https://github.com/lesterlo/mncos-manifest.git -b main
# Fetch all the source from the repositories in the manifest
repo sync
# OPTIONAL: Create a development branch on each repo
repo start <Your-Branch-Name> --all
```

# Reference
[Xilinx yocto-manifests](https://github.com/Xilinx/yocto-manifests)