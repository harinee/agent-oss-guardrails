# Python in Sensitive Environment

For Python projects in regulated or sensitive environments.

**Included:**
- OSS Selection Strict
- Agent Can Install Packages
- Python / pip Ecosystem
- Regulated / Sensitive Context

---

# OSS Selection Strict

## Core principles

- avoid newly published packages (less than 6 months old) unless well-justified
- avoid packages with single maintainer in critical dependency path
- pin to exact versions with no flexibility
- require all dependencies in manifest files with no exceptions
- forbid dynamic runtime downloads or installs
- forbid `curl | bash` or similar patterns
- require explicit approval for packages from unverified publishers

---

# Agent Can Install Packages

## Before installing

- provide clear explanation of why the package is needed
- explain what alternatives were considered
- highlight any risk signals
- wait for confirmation if risk signals are present

## Installation behavior

- install specific versions only (pip install package==1.2.3)
- ensure the package is recorded in requirements.txt
- update requirements files when dependencies change
- verify lockfile integrity after installation

---

# Python / pip Ecosystem

## Package selection

- prefer maintained libraries with active PyPI presence
- avoid packages with setup.py scripts that download additional code
- prefer pure Python packages when possible
- check PyPI download statistics and maintenance status
- avoid packages that are wrappers around unmaintained C libraries

## Version management

- pin exact versions in requirements.txt (package==1.2.3)
- use requirements.txt or poetry.lock for reproducibility
- commit lockfiles (requirements.txt, poetry.lock, Pipfile.lock)

## Virtual environments

- use virtual environments (venv, virtualenv, poetry env)
- avoid installing packages globally
- avoid modifying system Python installation

## Security

- avoid packages with known vulnerabilities
- be cautious of packages with native extensions from unknown publishers
- avoid packages that execute code during installation
- respect pip audit or safety check warnings

---

# Regulated / Sensitive Context

## Compliance requirements

- ensure dependencies comply with regulatory requirements
- document dependency compliance status
- maintain audit trails for dependency decisions
- verify license compatibility with regulatory constraints

## Explainability and auditability

- require clear rationale for every dependency
- document dependency decision-making process
- maintain comprehensive dependency inventory
- ensure all dependencies are auditable and traceable

## Security rigor

- require security assessments before adding dependencies
- prefer dependencies with security certifications or audits
- avoid dependencies with known vulnerabilities
- require sign-off for dependencies with elevated privileges

## Data handling

- verify that dependencies don't transmit sensitive data unexpectedly
- avoid dependencies with telemetry or analytics that could leak data
- review dependency network behavior
- ensure dependencies comply with data residency requirements

## Package restrictions

Avoid or require special approval for:
- newly published packages (less than 12 months)
- packages from single maintainers in critical paths
- packages without clear security policies
- packages that phone home or collect telemetry
- packages with unclear provenance
