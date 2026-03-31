# OSS Selection Baseline

Foundational guidance for selecting and managing open source dependencies, tools, and plugins.

## When to use this

Apply this baseline to all projects where AI agents may suggest, install, or manage dependencies.

## Instructions

### Dependency selection

- prefer well-maintained packages with recent commits and active maintainers
- avoid adding dependencies unless they provide clear value
- avoid introducing frameworks for simple tasks that can be solved with lightweight libraries
- prefer packages with clear documentation and established usage patterns
- avoid packages that duplicate functionality already present in the project
- prefer official packages from framework authors and trusted publishers
- verify package names carefully to avoid typosquatting

### Version management

- pin dependencies to specific versions (e.g., 1.2.3 not ^1.2.0 or latest)
- avoid using `latest` tags for container images
- avoid flexible version ranges that allow unpredictable updates
- record exact versions in lockfiles and commit them to version control
- update dependencies intentionally through explicit actions, not automatically

### Dependency visibility

- record all dependencies in standard manifest files (package.json, requirements.txt, pom.xml, etc.)
- ensure lockfiles are generated and kept up to date
- avoid git URL dependencies unless necessary
- avoid dynamic runtime downloads that bypass manifests
- ensure transitive dependencies are visible in lockfiles

### Package sources

- use official package registries (npm, PyPI, Maven Central, Docker Hub)
- avoid custom registries unless required by the project
- avoid downloading packages from arbitrary URLs
- avoid executing install scripts from unknown sources
- verify package authenticity when possible

### Installation practices

- respect existing lockfiles and dependency management conventions
- avoid deleting lockfiles to resolve dependency conflicts
- ensure new dependencies are recorded in both manifest and lockfile
- avoid modifying system configuration unnecessarily
- prefer package manager install commands over manual downloads

### Risk awareness

Before suggesting a dependency, highlight if:
- the package has no commits in the last 12 months
- the package has very few downloads or limited adoption
- the package comes from an unknown or unverified publisher
- the package requires elevated permissions or broad access
- the package is very new (published recently) without established track record

### Code execution

- avoid `curl | bash` patterns or piping URLs directly to shell
- avoid executing remote scripts without review
- avoid dynamic code evaluation (eval, exec) of fetched content
- prefer deterministic, reviewable installation processes

### Documentation

When adding dependencies, explain:
- why the dependency is needed
- what alternatives were considered
- what functionality it provides
- whether it introduces new frameworks or significant complexity

## Risk signals

If you encounter these signals, flag them to the user before proceeding:

- Package with no recent maintenance activity
- Package from unverified or unknown publisher
- Package requiring privileged access or broad permissions
- Git URL or direct download instead of registry package
- Dynamic runtime dependency loading
- Request to delete or bypass lockfiles
- Installation script that downloads additional code
