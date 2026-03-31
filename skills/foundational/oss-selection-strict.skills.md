# OSS Selection Strict

Stricter guardrails for production-critical, regulated, or high-security environments.

## When to use this

Apply this to projects with elevated security requirements, production systems, or regulated environments.

## Instructions

### Dependency selection (strict)

- avoid newly published packages (less than 6 months old) unless well-justified
- avoid packages with single maintainer in critical dependency path
- avoid packages with unclear or inactive maintenance
- prefer packages with established security response processes
- prefer packages with security audits or certifications where available
- avoid experimental or alpha/beta packages in production paths
- require clear justification for any new foundational framework

### Version management (strict)

- pin to exact versions with no flexibility
- avoid any use of version ranges or wildcards
- avoid `latest`, `main`, `master`, or branch references in container images
- require manual review before any dependency version update
- document version update rationale in commit messages

### Dependency visibility (strict)

- require all dependencies in manifest files with no exceptions
- avoid git URL dependencies unless absolutely required and explicitly approved
- avoid path dependencies that bypass package registries
- ensure every transitive dependency is captured in lockfiles
- forbid dynamic runtime downloads or installs
- forbid install scripts that fetch additional code

### Package sources (strict)

- require official registries only (npm, PyPI, Maven Central)
- avoid private or custom registries unless explicitly configured for the project
- verify publisher identity and reputation before adding packages
- avoid packages from publishers with no verified identity
- prefer packages with provenance information where available

### Installation practices (strict)

- never delete or modify lockfiles without explicit review
- never bypass package manager conventions
- avoid any system-level modifications
- require manifest and lockfile updates in the same commit
- forbid direct binary downloads

### Tools and plugins (strict)

- treat CI actions, build tools, and scanners as high-trust dependencies
- require review for any tool with code access or execution privileges
- prefer verified publishers for GitHub Actions and similar tools
- pin all tool and action versions exactly
- avoid tools with unnecessarily broad permissions

### Risk awareness (strict)

Require explicit approval before using:
- packages published within the last 6 months
- packages with fewer than 100 stars/downloads (adjust threshold by ecosystem)
- packages from single maintainers in critical paths
- packages with no security policy or disclosure process
- packages introducing new foundational frameworks
- any dependency outside standard registries

### Code execution (strict)

- forbid `curl | bash` or similar patterns
- forbid executing any remote scripts
- forbid dynamic code evaluation
- require static, auditable installation processes
- require sandboxing or isolation for any code execution during install

### Change management (strict)

When adding dependencies:
- provide detailed justification including alternatives considered
- assess security posture of the package and its maintainers
- document any elevated permissions or access requirements
- ensure dependency changes are reviewable in separate commits or PRs
- flag any high-impact changes explicitly

### License compliance (strict)

- avoid packages with unclear or missing licenses
- avoid licenses that conflict with project requirements
- document license compatibility before adding dependencies
- prefer permissive licenses (MIT, Apache 2.0, BSD) unless other licenses are explicitly approved

## Risk signals (strict)

Require explicit user approval before proceeding if:

- Package published within last 6 months
- Package has single maintainer
- Package from unverified publisher
- Package requires elevated privileges
- Git URL, branch reference, or direct download
- Dynamic runtime dependency loading
- Installation script executes additional downloads
- Unclear or incompatible license
- No security policy or contact
- Package introduces new foundational framework
- Adding tool with code execution or secret access
