SHELL     := bash
MAKEFLAGS += --warn-undefined-variables
.DEFAULT_GOAL = all

toolchain       = docker
check-toolchain := $(foreach cmd,$(toolchain), \
	$(if $(shell which $(cmd)),,$(error "Unable to find required '$(cmd)' on your $$PATH")))

docker      = $(shell command -v docker 2> /dev/null)
docker_args =

images_path := $(shell dirname $(realpath $(lastword $(MAKEFILE_LIST))))/images
images      := $(shell find $(images_path) -mindepth 1 -maxdepth 1 -type d -not -name images -exec basename {} \;)

all: $(images)
	@
.PHONY: all

pre-build:
	@
.PHONY: pre-build

build: pre-build .docker-build post-build
	@
.PHONY: build

post-build:
	@
.PHONY: post-build

.docker-build:
	@set -euxo pipefail && \
		$(docker) build -t "${IMAGE_NAME}:${IMAGE_VERSION}" \
			$(patsubst %,--build-arg %,$(BUILD_ARGS)) .
.PHONY: .docker-build

$(images):
	$(MAKE) -C "${images_path}/${@}" build
.PHONY: $(images)
