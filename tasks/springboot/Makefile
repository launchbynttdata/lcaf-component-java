SOURCE_FOLDER=source

.PHONY: run
run::
	@echo "Running Spring Boot application"
	./gradlew bootRun

.PHONY: dockerize
dockerize::
	@echo "Building Docker image"
	docker build -t springboot-app .

.PHONY: test
test::
	@echo "Running tests"
	./gradlew test

.PHONY: build
build::
	@echo "Building Spring Boot JAR"
	./gradlew build
