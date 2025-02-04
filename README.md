# Monutchee OS (MNCos) Project template


# Introduction

This is a project template for building yocto on Xilinx ZYNQ devices.

| Name                   | Description                                               | Link                                                 |
|------------------------|-----------------------------------------------------------|------------------------------------------------------|
| meta-manifest (This)   | Initialize the yocto building enviroment using repo tools | [Link](https://github.com/lesterlo/mncos-manifest)   |
| meta-mncos             | A yocto distro layer of the project                       | [Link](https://github.com/lesterlo/meta-mncos)       |
| mncos-scripts          | A helper repo to setup the yocto environment              | [Link](https://github.com/lesterlo/mncos-scripts)    |
| meta-zuboard           | A yocto hardware layer for Avnet ZUBoard                  | [Link](https://github.com/lesterlo/meta-zuboard)     |
| Vivado-Template        | Build the Vivado project for Programmable logic (PL)      | [Link](https://github.com/lesterlo/Vivado-Template)  |


# Build guide
For a more detailed build guide, please visit the [MNCos Wiki](https://github.com/lesterlo/mncos-manifest/wiki)

# Initialze the project

```bash
mkdir <your folder name>
cd <your folder name>
# Fetch the manifest and checkout the target release version
repo init -u https://github.com/lesterlo/mncos-manifest.git -b main
# Fetch all the source from the repositories in the manifest
repo sync


# OPTIONAL: Create a development branch on each repo
repo start <Your-Branch-Name> --all

# OPTIONAL: Set our repositories in branch HEAD rather than detected
repo forall <branch_names> -c 'git switch main'
```

# Reference
[Xilinx yocto-manifests](https://github.com/Xilinx/yocto-manifests)
