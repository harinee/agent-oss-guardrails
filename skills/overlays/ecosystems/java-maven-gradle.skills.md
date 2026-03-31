# Java / Maven / Gradle Ecosystem

Specific guidance for Java projects using Maven or Gradle.

## When to use this

Apply this overlay to Java projects.

## Instructions

### Package selection

- prefer libraries from Maven Central
- prefer well-established libraries with strong community support
- avoid snapshot versions in production
- check library maintenance status and update frequency
- prefer libraries from reputable organizations

### Version management

- pin exact versions in pom.xml or build.gradle
- avoid version ranges (e.g., [1.0,2.0)) in production
- avoid SNAPSHOT versions in production dependencies
- use dependency management sections to control transitive versions

### Repository configuration

- prefer Maven Central as primary repository
- avoid adding custom repositories unless necessary
- verify repository URLs before adding
- avoid repositories without HTTPS
- document why custom repositories are required

### Dependency scope

- use appropriate scopes (compile, test, provided, runtime)
- avoid including test dependencies in production builds
- keep test dependencies separate
- minimize compile-time dependencies

### Build files

- maintain consistent formatting in pom.xml or build.gradle
- avoid modifying parent POM configurations unnecessarily
- respect existing dependency management patterns
- update lockfiles (gradle.lockfile) when dependencies change

### Transitive dependencies

- be aware of transitive dependency chains
- use dependency exclusions carefully and document why
- avoid creating dependency conflicts
- review transitive dependencies for vulnerabilities

### Plugins and build tools

- treat Maven plugins and Gradle plugins as dependencies
- pin plugin versions exactly
- prefer official plugins from Maven or Gradle
- avoid plugins from unknown publishers

### Security

- avoid dependencies with known CVEs
- respect Maven dependency:analyze and dependency:tree warnings
- use dependency verification in Gradle when available
- avoid dependencies that download additional code at runtime
