# Mapping to Standards

This document maps the agent OSS guardrails to established standards, frameworks, and best practices in software supply chain security.

## OWASP

### OWASP Top 10 CI/CD Security Risks

These guardrails align with several OWASP CI/CD security risks:

**CICD-SEC-4: Poisoned Pipeline Execution (PPE)**
- Guardrails discourage unverified CI actions and build tools
- Pin versions for CI dependencies
- Review privileged tooling before introduction

**CICD-SEC-6: Insufficient Credential Hygiene**
- Treat MCP servers and connectors as privileged dependencies
- Review tool permissions and access scope
- Discourage broad-access tools

**CICD-SEC-8: Ungoverned Usage of 3rd Party Services**
- Prefer official registries and publishers
- Review external tools and connectors
- Ensure visibility of third-party integrations

### OWASP Dependency-Check and OWASP DependencyTrack

These guardrails complement SCA tools by:
- Reducing the likelihood of introducing problematic dependencies
- Encouraging version pinning for consistent scanning
- Ensuring dependencies remain discoverable for analysis

## SLSA (Supply-chain Levels for Software Artifacts)

### SLSA Framework Alignment

**Build Level 1: Provenance**
- Discourage dynamic downloads that lack provenance
- Prefer official sources with verifiable origins
- Encourage lockfiles that capture dependency provenance

**Build Level 2: Hosted Build**
- Pin CI action versions for reproducible builds
- Avoid unverified publishers in build pipelines
- Encourage predictable build behavior

**Build Level 3: Hardened Build**
- Strict version pinning
- Avoid dynamic dependency resolution
- Minimize dependencies to reduce supply chain complexity

## SBOM (Software Bill of Materials)

### Supporting SBOM Practices

These guardrails support SBOM generation and accuracy by:

**Ensuring visibility**: All dependencies should be in manifests and lockfiles, making SBOM generation complete and accurate

**Discouraging hidden dependencies**: Runtime downloads and dynamic imports are discouraged, preventing SBOM gaps

**Version specificity**: Pinned versions ensure SBOM accuracy

**Discouraging bypasses**: Avoiding git URLs and direct downloads keeps dependencies in standard formats

## NIST Secure Software Development Framework (SSDF)

### SSDF Practice Alignment

**PO.3: Ensure that third-party software is sufficiently secure**
- Review third-party dependencies before adoption
- Prefer well-maintained projects
- Apply scrutiny to tools and plugins

**PS.1: Protect all forms of code from unauthorized access**
- Review permissions of MCP servers, scanners, and tools
- Discourage broad-access connectors

**PS.3: Review and/or analyze code to identify vulnerabilities**
- Make dependency changes reviewable
- Ensure dependencies are discoverable for scanning
- Support SCA tool effectiveness

**PW.1: Design software to meet security requirements and mitigate security risks**
- Minimize dependencies to reduce attack surface
- Apply different guardrail levels based on risk context

## CIS Controls

### CIS Control 2: Inventory and Control of Software Assets

These guardrails support software inventory by:
- Ensuring dependencies are recorded in standard manifests
- Discouraging hidden or dynamic dependencies
- Promoting lockfile usage for complete inventories

### CIS Control 16: Application Software Security

These guardrails support secure development by:
- Encouraging selection of maintained, secure dependencies
- Discouraging bypasses of package manager security features
- Supporting vulnerability management through version pinning

## Software Composition Analysis (SCA)

### Complementing SCA Tools

These guardrails work alongside SCA tools:

**Before SCA**: Reduce the likelihood of introducing problematic dependencies

**During SCA**: Ensure dependencies are visible and scannable

**After SCA**: Make it easier to address findings through clear dependency provenance

Popular SCA tools include:
- Snyk
- Dependabot
- WhiteSource/Mend
- Black Duck
- OWASP Dependency-Check

These guardrails do not replace SCA but make it more effective by:
- Reducing noise from unnecessary dependencies
- Ensuring complete visibility
- Supporting remediation through version pinning

## License Compliance

### Supporting License Management

**SPDX (Software Package Data Exchange)**: Guardrails encourage manifest-based dependencies that support SPDX SBOM generation

**ClearlyDefined**: Preferring official packages from known publishers improves license clarity

**License scanning**: Discouraging hidden dependencies ensures license scanners see all components

**Regulated contexts**: The regulated-sensitive overlay encourages avoiding unclear licensing

## ISO/IEC Standards

### ISO/IEC 27001: Information Security Management

**A.14.2.1 Secure development policy**: These guardrails provide practical agent-consumable implementation of secure development practices

**A.14.2.5 Secure system engineering principles**: Minimal dependencies and secure defaults align with secure engineering

### ISO/IEC 27034: Application Security

**Organizational Normative Framework (ONF)**: These skills files can be part of an organization's application security framework

**Application Security Controls**: Guardrails implement specific controls for dependency management

## EU Cyber Resilience Act (CRA)

The proposed CRA emphasizes secure-by-design principles:

**Supply chain security**: These guardrails help organizations demonstrate due diligence in dependency selection

**Vulnerability handling**: Version pinning and maintained dependencies support vulnerability management obligations

**Security requirements**: Different overlay levels support varied risk contexts

## Industry Best Practices

### Google's "Know, Prevent, Fix" Framework

**Know**: Ensure dependencies are discoverable and inventoried

**Prevent**: Reduce introduction of problematic dependencies upfront

**Fix**: Enable rapid response through version pinning and manifest clarity

### Microsoft's Security Development Lifecycle (SDL)

**Secure by design**: Minimal dependencies reduce attack surface

**Secure by default**: Baseline guardrails provide secure defaults

**Secure in deployment**: Version pinning and reproducibility support secure deployment

### CNCF Supply Chain Security Best Practices

**Use minimal base images**: Container overlay encourages minimal images

**Pin versions**: Discourage `latest` tags

**Verify provenance**: Prefer official images with clear provenance

## Conclusion

These agent OSS guardrails complement, rather than replace, existing standards and tools. They provide a practical, agent-consumable implementation layer that:

✓ Aligns with established frameworks
✓ Supports automated tooling (SCA, SBOM)
✓ Implements secure-by-design principles
✓ Adapts to different risk contexts
✓ Remains practical for agent interpretation

By translating high-level standards into specific agent behaviors, these guardrails help bridge the gap between security policy and day-to-day development with AI assistance.
