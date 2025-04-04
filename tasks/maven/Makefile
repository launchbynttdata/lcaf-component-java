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
	@echo "Generating GitHub token..."
	@GITHUB_APPLICATION_ID=$$(aws secretsmanager get-secret-value --secret-id github/app/aws-pipeline-authentication/application_id --query SecretString --output text); \
	INSTALLATION_ID=$$(aws secretsmanager get-secret-value --secret-id github/app/aws-pipeline-authentication/installation_id --query SecretString --output text); \
	PRIVATE_KEY_SECRET=github/app/aws-pipeline-authentication/private_key; \
	GITHUB_TOKEN=$$(launch github auth application \
		--application-id-parameter-name $$GITHUB_APPLICATION_ID \
		--installation-id-parameter-name $$INSTALLATION_ID \
		--signing-cert-secret-name $$PRIVATE_KEY_SECRET); \
	echo "Creating temporary settings.xml"; \
	echo "<settings><servers><server><id>github</id><username>github</username><password>$$GITHUB_TOKEN</password></server></servers></settings>" > temp-settings.xml; \
	./mvnw deploy --settings temp-settings.xml; \
	rm -f temp-settings.xml

.PHONY: publish
publish:: build
	@echo "Running publish target"
	@./mvnw deploy

.PHONY: version
version::
	@echo "Running version target"
	@./mvnw versions:set -DnewVersion=$(TAG)
