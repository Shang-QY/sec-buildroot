# Targets
all: docker_rootfs

layers := $(CURDIR)/layers

docker_image.tar.gz:
	docker pull riscv64/buildpack-deps:unstable
	docker save -o docker_image.tar.gz riscv64/buildpack-deps:unstable

$(layers): docker_image.tar.gz
	mkdir -p layers
	tar -xf $(CURDIR)/docker_image.tar.gz -C layers

docker_rootfs: $(layers)
	mkdir -p penglai_rootfs
	for file in $$(jq -r '.[0].Layers[]' layers/manifest.json); do \
		tar -xf "layers/$$file" -C penglai_rootfs; \
	done

clean:
	rm -rf penglai_rootfs
	rm -rf layers
