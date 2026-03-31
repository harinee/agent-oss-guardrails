# Baseline General Purpose

A general-purpose baseline combining foundational guidance with common capability overlays.

**Included:**
- OSS Selection Baseline
- Agent Can Install Packages
- Agent Can Run Shell

---

# OSS Selection Baseline

## Dependency selection

- prefer well-maintained packages with recent commits and active maintainers
- avoid adding dependencies unless they provide clear value
- avoid introducing frameworks for simple tasks that can be solved with lightweight libraries
- prefer packages with clear documentation and established usage patterns
- avoid packages that duplicate functionality already present in the project
- prefer official packages from framework authors and trusted publishers
- verify package names carefully to avoid typosquatting

## Version management

- pin dependencies to specific versions (e.g., 1.2.3 not ^1.2.0 or latest)
- avoid using `latest` tags for container images
- avoid flexible version ranges that allow unpredictable updates
- record exact versions in lockfiles and commit them to version control
- update dependencies intentionally through explicit actions, not automatically

## Dependency visibility

- record all dependencies in standard manifest files (package.json, requirements.txt, pom.xml, etc.)
- ensure lockfiles are generated and kept up to date
- avoid git URL dependencies unless necessary
- avoid dynamic runtime downloads that bypass manifests
- ensure transitive dependencies are visible in lockfiles

## Package sources

- use official package registries (npm, PyPI, Maven Central, Docker Hub)
- avoid custom registries unless required by the project
- avoid downloading packages from arbitrary URLs
- avoid executing install scripts from unknown sources
- verify package authenticity when possible

## Installation practices

- respect existing lockfiles and dependency management conventions
- avoid deleting lockfiles to resolve dependency conflicts
- ensure new dependencies are recorded in both manifest and lockfile
- avoid modifying system configuration unnecessarily
- prefer package manager install commands over manual downloads

## Risk awareness

Before suggesting a dependency, highlight if:
- the package has no commits in the last 12 months
- the package has very few downloads or limited adoption
- the package comes from an unknown or unverified publisher
- the package requires elevated permissions or broad access
- the package is very new (published recently) without established track record

## Code execution

- avoid `curl | bash` patterns or piping URLs directly to shell
- avoid executing remote scripts without review
- avoid dynamic code evaluation (eval, exec) of fetched content
- prefer deterministic, reviewable installation processes

---

# Agent Can Install Packages

## Before installing

- provide clear explanation of why the package is needed before installing
- explain what alternatives were considered
- highlight any risk signals (new package, unknown publisher, etc.)
- wait for confirmation if risk signals are present

## Installation behavior

- prefer modifying existing dependencies over adding new ones
- avoid installing packages speculatively or "just in case"
- install specific versions, not latest or version ranges
- ensure the package is recorded in manifest files
- ensure lockfiles are updated when packages are installed

---

# Agent Can Run Shell

## Avoid risky patterns

- avoid `curl | bash` or `wget | sh` patterns
- avoid piping URLs directly to shell interpreters
- avoid executing remote scripts without review
- avoid downloading and executing binaries from arbitrary URLs
- prefer package manager commands over manual downloads
- avoid modifying system configuration unnecessarily
