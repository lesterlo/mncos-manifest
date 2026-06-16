

# Project dir Initialization

The following command will download and initialze a the workspace for you

```bash
curl -fsSL "https://raw.githubusercontent.com/lesterlo/mncos-manifest/main/zudemo/zudemo-setupWorkspace" | bash -s -- all
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
```


# Build Steps

## PL

## APU

## RPU

## Yocto



1. load and prepare the yocto buuild environment

    ```bash
    cd yocto-build && source ./setupSDK

    ```

1. run gen-machineconf
    ```bash
    gen-machineconf parse-sdt \
         --hw-description /opt/monutchee/zudemo/runtime-generated/vivado_SDT_out/ \
         -c conf -D \
         -g full --machine-name "zudemo" \
         --add-config CONFIG_YOCTO_BBMC_CORTEXR5_0_FREERTOS=y \
         --add-config CONFIG_YOCTO_BBMC_CORTEXR5_1_FREERTOS=y \
         --domain-file ../sources/meta-zuboard/recipes-bsp/domainyaml/openamp-overlay-zynqmp.yaml
    ```
1. After the machine config generate
    
    Modify the `build/conf/local.conf` . Change the machine name to "zudemo"
    ```bash
    MACHINE = "zudemo"
    ```

1. build the yocto image

    ```bash
    bitbake mncos-image-minimal
    ```

Please refer to [Wiki](https://github.com/lesterlo/mncos-manifest/wiki/04.-Build-the-yocto-image) for main reference.