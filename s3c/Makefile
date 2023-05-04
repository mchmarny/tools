IMAGENAME := s3c-tools
VERSION   :=$(shell cat .version)
USERNAME  :=$(shell git config user.username)

## Variable assertions
ifndef VERSION
	$(error VERSION is not set)
endif

all: help

.PHONY: version
version: ## Prints the current version
	@echo $(VERSION)

.PHONY: build
build: ## Builds docker image
	docker build \
		-t ghcr.io/$(USERNAME)/$(IMAGENAME):$(VERSION) \
		.

.PHONY: push
push: build ## Builds and pushes docker image
	docker push ghcr.io/$(USERNAME)/$(IMAGENAME):$(VERSION)
		
.PHONY: help
help: ## Display available commands
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | awk \
		'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'
