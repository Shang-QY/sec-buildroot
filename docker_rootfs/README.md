# Use one docker image as customized rootfs

Introduce the process of making and installing customized rootfs from a single ready-made docker image.

## Make

Using the ready-made docker image on docker hub: https://hub.docker.com/r/riscv64/buildpack-deps as an example. It has five layers and is used for general purpose. Its size is 1.1GB.

### Phase 1: Customer save their docker image customized for their business
```
docker pull riscv64/buildpack-deps:unstable

docker save -o docker_image.tar.gz riscv64/buildpack-deps:unstable
```

### Phase 2: Nanhu use this image as the customized rootfs in TEE

Put the `docker_image.tar.gz` in this directory.

## Install

Edit the config file `Penglai-secure-world/starfive-secure-linux/config/buildroot_initramfs_config` and make the setting of two configuration items same as the code block shown below:

```
# BR2_PENGLAI_CUSTOM_ROOTFS is not set
BR2_PENGLAI_DOCKER_ROOTFS=y
```
