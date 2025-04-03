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
publish::
	@echo "Running publish target"
	@./mvnw deploy

.PHONY: version
version::
	@echo "Running version target"
	@./mvnw versions:set -DnewVersion=$(TAG)
