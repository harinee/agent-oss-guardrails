# npm with High Autonomy Agent

For Node.js projects with highly autonomous agents.

**Included:**
- OSS Selection Baseline
- Agent Can Install Packages
- Agent Can Run Shell
- Agent Can Use Tools or MCP
- Agent Can Open PRs
- npm / Node.js Ecosystem

---

# OSS Selection Baseline

## Core principles

- prefer well-maintained packages with recent commits and active maintainers
- avoid adding dependencies unless they provide clear value
- avoid introducing frameworks for simple tasks
- pin dependencies to specific versions (e.g., 1.2.3 not ^1.2.0 or latest)
- record all dependencies in standard manifest files
- ensure lockfiles are generated and kept up to date
- use official package registries (npm, PyPI, Maven Central, Docker Hub)
- avoid `curl | bash` patterns or piping URLs directly to shell

## Risk awareness

Before suggesting a dependency, highlight if:
- the package has no commits in the last 12 months
- the package has very few downloads or limited adoption
- the package comes from an unknown or unverified publisher
- the package requires elevated permissions or broad access
- the package is very new without established track record

---

# Agent Capabilities

## Install packages

- provide clear explanation before installing
- explain what alternatives were considered
- install specific versions (npm install package@1.2.3)
- ensure package.json and lockfile are updated

## Run shell

- avoid `curl | bash` or `wget | sh` patterns
- avoid executing remote scripts without review
- prefer npm commands over manual downloads

## Use tools or MCP

- treat tools and MCP servers as dependencies
- verify publisher reputation before use
- review tool permissions and access requirements
- pin tool and MCP server versions

## Open PRs

- include clear explanation of dependency changes
- document why each new dependency was added
- flag high-impact changes
- keep dependency changes separate from unrelated code changes

---

# npm / Node.js Ecosystem

## Package selection

- prefer widely-used libraries with strong community adoption
- avoid adding heavy framework dependencies for simple tasks
- prefer native Node.js APIs when sufficient
- avoid packages that have been abandoned or deprecated
- check npm download counts and maintenance status

## Version management

- pin exact versions in package.json or use lockfiles
- commit package-lock.json, yarn.lock, or pnpm-lock.yaml
- avoid using `^` or `~` in version specifiers for production dependencies
- use exact versions for security-sensitive dependencies

## Dependencies vs devDependencies

- ensure packages are in the correct section
- avoid installing dev dependencies in production builds
- keep devDependencies separate from runtime dependencies

## Installation commands

- use `npm ci` for reproducible builds in CI/CD
- prefer `npm install package@1.2.3` with exact versions
- avoid `npm install` without version specifiers
- avoid `--force` flag unless explicitly needed and justified

## Security

- avoid packages with known vulnerabilities
- respect npm audit warnings
- avoid packages that make unexpected network requests
- be cautious of packages with install scripts (preinstall, postinstall)

## Node_modules

- never commit node_modules to version control
- rely on lockfiles for reproducibility
- avoid modifying files in node_modules directly
