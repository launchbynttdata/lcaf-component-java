SOURCE_FOLDER=source

.PHONY: clean
clean::
	@echo "Cleaning project"
	mvn clean

.PHONY: format
format::
	@echo "Running code formatter (using spotless or fmt-maven-plugin)"
	mvn fmt:format

.PHONY: lint
lint::
	@echo "Running lint check"
	mvn checkstyle:check

.PHONY: dependencies
dependencies::
	@echo "Listing dependencies"
	mvn dependency:tree
