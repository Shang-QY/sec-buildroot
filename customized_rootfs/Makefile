# Targets
all: penglai_rootfs

layers := $(CURDIR)/layers

$(layers):
	mkdir -p layers
	mkdir -p layers/docker_toolchain_image
	wget -P layers/docker_toolchain_image http://106.14.179.121/buildroot/docker_toolchain_image/rootfs.tar
	mkdir -p layers/python
	wget -P layers/python http://106.14.179.121/buildroot/python/rootfs.tar
	mkdir -p layers/numpy
	wget -P layers/numpy http://106.14.179.121/buildroot/numpy/numpy_module.tar

penglai_rootfs: $(layers)
	mkdir penglai_rootfs
# docker_toolchain_image is base layer, ubuntu environment with build toolchain
	tar -xf layers/docker_toolchain_image/rootfs.tar -C penglai_rootfs
# python layer contains python v3.9.7 with pip installed
	tar -xf layers/python/rootfs.tar -C penglai_rootfs
# numpy layer contains numpy module
	tar -xf layers/numpy/numpy_module.tar -C penglai_rootfs

clean:
	rm -rf penglai_rootfs
