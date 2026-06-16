



# Steps

## PL

## APU

## RPU

## Yocto


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