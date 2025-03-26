SOURCE_FOLDER=source
DIST_FOLDER=build/libs

.PHONY: install
install::
	@echo "Running install target"
	./gradlew clean build -x test

.PHONY: test
test:: install
	@echo "Running test target"
	./gradlew test

.PHONY: build
build:: install
	@echo "Running build target"
	./gradlew build

.PHONY: publish
publish::
	@echo "Running publish target"
	./gradlew publish

.PHONY: version
version::
	@echo "Running version target"
	./gradlew versions:set -PnewVersion=$(TAG)
