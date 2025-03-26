SOURCE_FOLDER=source
DIST_FOLDER=target

.PHONY: install
install::
	@echo "Running install target"
	mvn clean install

.PHONY: test
test:: install
	@echo "Running test target"
	mvn test

.PHONY: build
build:: install
	@echo "Running build target"
	mvn package

.PHONY: publish
publish::
	@echo "Running publish target"
	mvn deploy

.PHONY: version
version::
	@echo "Running version target"
	mvn versions:set -DnewVersion=$(TAG)
