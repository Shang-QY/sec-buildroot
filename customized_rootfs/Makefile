# Targets
all: penglai_rootfs

packages:
	mkdir -p layers
	mkdir -p layers/docker_toolchain_image
	pushd layers/numpy && wget http://106.14.179.121/buildroot/docker_toolchain_image/rootfs.tar && popd
	mkdir -p layers/python
	pushd layers/numpy && wget http://106.14.179.121/buildroot/python/rootfs.tar && popd
	mkdir -p layers/numpy
	pushd layers/numpy && wget http://106.14.179.121/buildroot/numpy/numpy_module.tar && popd

penglai_rootfs: packages
	mkdir penglai_rootfs
# docker_toolchain_image is base layer, ubuntu environment with build toolchain
	tar -xf layers/docker_toolchain_image/rootfs.tar -C penglai_rootfs
# python layer contains python v3.9.7 with pip installed
	tar -xf layers/python/rootfs.tar -C penglai_rootfs
# numpy layer contains numpy module
	tar -xf layers/numpy/numpy_module.tar -C penglai_rootfs

clean:
	rm -rf penglai_rootfs
