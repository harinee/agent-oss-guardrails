# Regulated / Sensitive Context

Strictest guidance for regulated industries, sensitive data, or high-security environments.

## When to use this

Apply this overlay to regulated environments (healthcare, finance, government), systems handling sensitive data, or high-security requirements.

## Instructions

### Compliance requirements

- ensure dependencies comply with regulatory requirements
- document dependency compliance status
- maintain audit trails for dependency decisions
- verify license compatibility with regulatory constraints

### Explainability and auditability

- require clear rationale for every dependency
- document dependency decision-making process
- maintain comprehensive dependency inventory
- ensure all dependencies are auditable and traceable

### Security rigor

- require security assessments before adding dependencies
- prefer dependencies with security certifications or audits
- avoid dependencies with known vulnerabilities
- require sign-off for dependencies with elevated privileges

### Data handling

- verify that dependencies don't transmit sensitive data unexpectedly
- avoid dependencies with telemetry or analytics that could leak data
- review dependency network behavior
- ensure dependencies comply with data residency requirements

### Vendor assessment

- assess dependency publishers and maintainers
- prefer dependencies from established, verifiable entities
- avoid dependencies from unknown or unvetted publishers
- document vendor assessment results

### Change control

- require formal approval for dependency changes
- follow change control procedures for dependency updates
- test dependency changes in isolated environments first
- maintain rollback plans for all dependency changes

### License compliance

- avoid dependencies with unclear or incompatible licenses
- document license compliance for all dependencies
- prefer permissive licenses that meet regulatory requirements
- obtain legal review for unusual licenses

### Package restrictions

Avoid or require special approval for:
- newly published packages (less than 12 months)
- packages from single maintainers in critical paths
- packages without clear security policies
- packages that phone home or collect telemetry
- packages with unclear provenance

### Incident response

- maintain incident response plan for dependency issues
- have process for rapidly responding to dependency vulnerabilities
- maintain contact information for dependency maintainers
- document escalation procedures for supply chain incidents
