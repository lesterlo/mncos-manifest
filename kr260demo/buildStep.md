

# Project dir Initialization

The following command will download and initialze a the workspace for you

```bash
curl -fsSL "https://raw.githubusercontent.com/lesterlo/monutchee-manifest/main/kr260demo/kr260demo-setupWorkspace" | bash -s -- all
```

# VS Code initialization

Add the following lines to `.vscode/settings.json` to prevent to many yocto files generate crash the vscode

```
    "files.exclude": {
        "yocto-build/build/**": false
    },
    "search.exclude": {
        "yocto-build/build/**": true
    },
    "files.watcherExclude": {
        "**/yocto-build/build/**": true
    },
    "C_Cpp.files.exclude": {
        "**/yocto-build/build/**": true
    },
    "git.ignoredRepositories": [
        "yocto-build/sources/meta-arm",
        "yocto-build/sources/meta-kria",
        "yocto-build/sources/meta-openamp",
        "yocto-build/sources/meta-openembedded",
        "yocto-build/sources/meta-virtualization",
        "yocto-build/sources/meta-xilinx",
        "yocto-build/sources/poky"
    ],
    "git.scanRepositories": [
        "yocto-build/sources/meta-monutchee"
    ]
```


# Build Steps

## PL

## APU

## RPU

## Yocto


### Build step
1. load and prepare the yocto buuild environment

    ```bash
    cd yocto-build && source ./setupSDK

    ```

1. run gen-machineconf
    ```bash
    #Assume your are in yocto-build/build
    gen-machineconf parse-sdt \
         --hw-description ../../runtime-generated/vivado_SDT_out/ \
         -c conf -D \
         -g full --machine-name "kr260demo" \
         --add-config CONFIG_YOCTO_BBMC_CORTEXR5_0_FREERTOS=y \
         --add-config CONFIG_YOCTO_BBMC_CORTEXR5_1_FREERTOS=y \
         --domain-file ../sources/meta-monutchee/meta-zuboard/recipes-bsp/domainyaml/openamp-overlay-zynqmp.yaml
    ```
1. After the machine config generate
    
    Modify the `build/conf/local.conf` . Change the machine name to "kr260demo"
    ```bash
    MACHINE = "kr260demo"
    ```

1. build the yocto image

    ```bash
    bitbake zuboard-image-minimal
    ```

Please refer to [Wiki](https://github.com/lesterlo/monutchee-manifest/wiki/04.-Build-the-yocto-image) for main reference.

### Advance configuration

To config the yocto use the local compiled binary, insert the following line to `conf/local.conf`
```bash
APU_RPU_CTL_SRC = "local"
ZUBOARD_FIRMWARE_SRC = "local"
APU_RPU_CTL_GIT_BRANCH = "main"
```
