# TDD Adapter: Java

## Detection

- Maven: `pom.xml`
- Gradle: `build.gradle`, `settings.gradle`, `build.gradle.kts`

## Test Strategy

- Prefer existing JUnit, TestNG, Mockito, or Spring test conventions.
- Place tests under `src/test/java` unless the project uses another convention.
- Use module-scoped test commands in multi-module repositories.

## Commands

- Maven focused test: `mvn -Dtest=<TestClass>#<testMethod> test`
- Maven module test: `mvn -pl <module> -Dtest=<TestClass> test`
- Gradle test: `./gradlew test`

## Review Risks

- Tests requiring external services.
- Spring context tests used where unit tests would be enough.
- Multi-module dependency drift.
