# lcaf-component-java-library

This repository holds the  component for Java library modules within the Launch Common Automation Framework (LCAF). It is intended to be widely compatible with the broad array of Java build tools and frameworks by separating framework-specific tasks into their own Makefiles. Targets that are generalized across multiple frameworks should be placed in the Makefile under `tasks/common`.

This component contains the following:

* **linkfiles** – Common config files used by Java and LCAF projects (e.g., `pom.xml`, `build.gradle`, `.gitignore`, etc.)
* **tasks** – Makefiles for performing operations like building, testing, publishing, and versioning, broken down by tool and framework. A selection of popular frameworks (Spring Boot, Maven, Gradle) is provided as a starting point. This can be extended or reduced as frameworks gain or lose popularity.
  * Framework-specific targets should be prefixed accordingly. For example, in `tasks/springboot/Makefile`, finding a `springboot/run` target is acceptable. If the `run` target is generic enough to apply across frameworks, it should live in `tasks/common/Makefile`.

