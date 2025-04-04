# Set JAVA_HOME using asdf
JAVA_HOME := $(shell asdf where java)
export JAVA_HOME
export PATH := $(JAVA_HOME)/bin:$(PATH)

$(info JAVA_HOME set to: $(JAVA_HOME))

.PHONY: install
install::
	@echo "Running install target"
	@./mvnw install

.PHONY: test
test:: install
	@echo "Running test target"
	@./mvnw test

.PHONY: build
build:: install
	@echo "Running build target"
	@./mvnw package

.PHONY: publish
publish:: build
	@echo "Running publish target"
	@./mvnw deploy

.PHONY: version
version::
	@echo "Running version target"
	@./mvnw versions:set -DnewVersion=$(TAG)
