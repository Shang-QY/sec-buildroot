# Targets
all: penglai_rootfs

penglai_rootfs:
	mkdir penglai_rootfs
# docker_toolchain_image is base layer, ubuntu environment with build toolchain
	tar -xf layers/docker_toolchain_image/rootfs.tar -C penglai_rootfs
# python layer contains python v3.9.7 with pip installed
	tar -xf layers/python/rootfs.tar -C penglai_rootfs
# numpy layer contains numpy module
	tar -xf layers/numpy/numpy_module.tar -C penglai_rootfs

clean:
	rm -rf penglai_rootfs
