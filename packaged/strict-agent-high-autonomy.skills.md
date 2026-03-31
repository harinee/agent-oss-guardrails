# Strict Agent with High Autonomy

For highly autonomous agents with broad capabilities in sensitive or production environments.

**Included:**
- OSS Selection Strict
- Agent Can Install Packages
- Agent Can Run Shell
- Agent Can Use Tools or MCP
- Agent Can Open PRs
- Production Context

---

# OSS Selection Strict

## Dependency selection (strict)

- avoid newly published packages (less than 6 months old) unless well-justified
- avoid packages with single maintainer in critical dependency path
- avoid packages with unclear or inactive maintenance
- prefer packages with established security response processes
- require clear justification for any new foundational framework

## Version management (strict)

- pin to exact versions with no flexibility
- avoid any use of version ranges or wildcards
- avoid `latest`, `main`, `master`, or branch references
- require manual review before any dependency version update
- document version update rationale in commit messages

## Dependency visibility (strict)

- require all dependencies in manifest files with no exceptions
- avoid git URL dependencies unless absolutely required and explicitly approved
- forbid dynamic runtime downloads or installs
- forbid install scripts that fetch additional code

## Code execution (strict)

- forbid `curl | bash` or similar patterns
- forbid executing any remote scripts
- forbid dynamic code evaluation
- require static, auditable installation processes

## Risk signals (strict)

Require explicit user approval before proceeding if:
- Package published within last 6 months
- Package has single maintainer
- Package from unverified publisher
- Package requires elevated privileges
- Git URL, branch reference, or direct download
- Package introduces new foundational framework

---

# Agent Capabilities

## Install packages

- provide clear explanation before installing
- highlight any risk signals and wait for confirmation
- install specific versions only
- ensure lockfiles are updated

## Run shell

- forbid `curl | bash` patterns
- avoid executing remote scripts
- prefer package manager commands
- avoid system-wide modifications

## Use tools or MCP

- treat tools and MCP servers as dependencies
- verify publisher reputation before use
- review permissions and access requirements
- pin tool and MCP server versions
- document what MCP servers are installed and why

## Open PRs

- include clear explanation of dependency changes in PR descriptions
- document why each new dependency was added
- flag high-impact changes (frameworks, privileged tools)
- keep dependency changes separate from unrelated changes

---

# Production Context

## Stability priority

- prefer stable, well-tested releases
- avoid experimental or alpha/beta packages
- treat dependency changes as significant events requiring review
- test dependency updates thoroughly before production deployment

## Version management

- pin exact versions with no flexibility
- document version selection rationale
- maintain dependency update changelog

## Rollback readiness

- ensure dependency changes can be rolled back
- test rollback procedures
- maintain previous known-good dependency versions
