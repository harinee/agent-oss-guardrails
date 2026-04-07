# 📊 Mapping to Standards

> How Agent OSS Guardrails align with established security frameworks

---

## Overview

These guardrails are a **practical implementation layer** that translates high-level security standards into agent-consumable instructions. They complement (not replace) established frameworks.

---

## 🏆 SLSA (Supply-chain Levels for Software Artifacts)

### Alignment by Level

| SLSA Level | How Guardrails Help |
|-----------|---------------------|
| **Build L1** | Discourage dynamic downloads lacking provenance; prefer official sources |
| **Build L2** | Pin CI action versions for reproducible builds; avoid unverified publishers |
| **Build L3** | Strict version pinning; avoid dynamic resolution; minimize dependencies |
| **Build L4** | Make changes reviewable; document rationale; separate commits |

**Example:**
```yaml
# ❌ Unpinned (violates reproducibility)
- uses: actions/checkout@main

# ✅ Pinned to commit SHA (SLSA L2+)
- uses: actions/checkout@8e5e7e5ab8b370d6c329ec480221332ada57f0ab
```

**Reference:** [SLSA Framework](https://slsa.dev/)

---

## 🔒 OWASP

### Top 10 CI/CD Security Risks

**CICD-SEC-4: Poisoned Pipeline Execution (PPE)**
- **Guardrails:** Discourage unverified CI actions, pin versions, review privileged tooling
- **Overlay:** `ci-actions-build-tools.skills.md`

**CICD-SEC-6: Insufficient Credential Hygiene**
- **Guardrails:** Treat MCP servers as privileged; review tool permissions/access scope
- **Overlays:** `mcp-servers-connectors.skills.md`, `agent-can-use-tools-or-mcp.skills.md`

**CICD-SEC-8: Ungoverned 3rd Party Services**
- **Guardrails:** Prefer official registries, review external tools, ensure visibility
- **Overlays:** All capability and artifact-type overlays

### Complementing OWASP Tools

| OWASP Tool | Guardrail Role |
|-----------|----------------|
| **Dependency-Check** | Prevent problematic deps upfront |
| **DependencyTrack** | Ensure discoverability for tracking |

**Together:** Guardrails reduce tool noise; tools catch what slips through.

**Reference:** [OWASP Top 10 CI/CD Risks](https://owasp.org/www-project-top-10-ci-cd-security-risks/)

---

## 🛡️ NIST Secure Software Development Framework (SSDF)

| SSDF Practice | Guardrail Implementation |
|--------------|-------------------------|
| **PO.3:** Ensure third-party software is secure | Review dependencies; prefer maintained projects; scrutinize tools |
| **PS.1:** Protect from unauthorized access | Review MCP/scanner permissions; discourage broad-access tools |
| **PS.3:** Review and analyze code | Make changes reviewable; ensure discoverability for scanning |
| **PW.1:** Design to meet security requirements | Minimize dependencies; adapt guardrails to risk context |

**Reference:** [NIST SSDF](https://csrc.nist.gov/Projects/ssdf)

---

## 📋 SBOM (Software Bill of Materials)

### Supporting SBOM Generation

| SBOM Need | How Guardrails Help |
|-----------|---------------------|
| **Completeness** | All deps in manifests; no hidden dependencies |
| **Accuracy** | Version pinning ensures SBOM reflects actual code |
| **Discoverability** | Standard formats; avoid git URLs |
| **Transitive deps** | Lockfiles capture full tree; no runtime downloads |

**Example:**
```javascript
// ❌ SBOM-hostile
{
  "dependencies": {
    "tool": "git+https://github.com/user/repo.git",
    "lib": "latest"
  },
  "postinstall": "curl https://cdn.com/setup.sh | bash"
}

// ✅ SBOM-friendly
{
  "dependencies": {
    "tool": "2.1.3",
    "lib": "1.0.0"
  }
}
```

**Reference:** [NTIA SBOM Minimum Elements](https://www.ntia.gov/report/2021/minimum-elements-software-bill-materials-sbom)

---

## 🔍 CIS Controls

**Control 2: Software Asset Inventory**
- Ensure deps in manifests; discourage hidden dependencies; promote lockfiles

**Control 16: Application Software Security**
- Encourage maintained deps; discourage package manager bypasses; support vulnerability management

**Reference:** [CIS Controls v8](https://www.cisecurity.org/controls/v8)

---

## 🌐 ISO/IEC Standards

**ISO/IEC 27001: Information Security Management**
- A.14.2.1: Secure development policy implementation
- A.14.2.5: Secure engineering principles (minimal deps, secure defaults)

**ISO/IEC 27034: Application Security**
- Guardrails as part of Organizational Normative Framework (ONF)
- Specific controls for dependency management

**Reference:** [ISO/IEC 27001](https://www.iso.org/isoiec-27001-information-security.html)

---

## 🇪🇺 EU Cyber Resilience Act (CRA)

| CRA Principle | Guardrail Support |
|--------------|-------------------|
| **Supply chain security** | Due diligence in dependency selection |
| **Vulnerability handling** | Version pinning enables rapid updates |
| **Security requirements** | Different overlay levels for varied risks |
| **Documentation** | Reviewable changes create audit trail |

**Reference:** [EU Cyber Resilience Act](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act)

---

## 🔧 Integration with Security Tools

| Tool Type | Examples | Guardrail Role |
|-----------|----------|---------------|
| **SCA** | Snyk, Dependabot | Reduce noise; ensure visibility |
| **SAST** | SonarQube, Checkmarx | Minimize code via dependency reduction |
| **SBOM** | Syft, CycloneDX | Ensure completeness via manifest discipline |
| **Policy** | OPA, Kyverno | Agent-level enforcement complementing policy |
| **Secrets** | GitGuardian, TruffleHog | Reduce risk via tool permission review |

**The Stack:**
```
POLICY ENGINES (OPA) → Organizational policies
        ↓
AGENT GUARDRAILS → Prevent bad choices
        ↓
SCA / SBOM / SAST → Detection & cataloging
        ↓
HUMAN REVIEW → Final checkpoint
```

---

## 📈 Measuring Alignment

**Supply Chain Health Metrics:**
- % deps with exact version pins
- % deps from verified publishers
- Average dependency age (last commit)
- Hidden/dynamic dependencies (should be 0)

**Process Compliance:**
- % dep changes with documentation
- % high-risk changes flagged
- Time between dependency updates

**Tool Effectiveness:**
- SBOM completeness scores
- SCA false positive rate (should decrease)
- Vulnerability response time

---

## 🎯 Compliance Summary

| Standard | Primary Alignment | Key Overlays |
|----------|------------------|--------------|
| **SLSA** | Build levels 1-3 | All |
| **OWASP** | CI/CD risks | `ci-actions`, `scanners` |
| **NIST SSDF** | PO.3, PS.1, PS.3, PW.1 | Foundational + contexts |
| **SBOM** | Completeness | All |
| **CIS** | Controls 2, 16 | Foundational |
| **ISO 27001** | A.14.2.x | All |
| **CRA** | Secure-by-design | `regulated-sensitive` |

---

## 🚀 Next Steps

**For Compliance Teams:**
1. Map requirements to standards
2. Select overlays supporting compliance
3. Document alignment
4. Track metrics
5. Iterate as standards evolve

**For Security Teams:**
1. Integrate with existing tools
2. Define metrics
3. Review effectiveness
4. Share learnings

**For Development Teams:**
1. Understand applicable standards
2. Apply appropriate level
3. Monitor agent behavior
4. Provide feedback

---

## 📚 Additional Resources

- [SLSA Specification](https://slsa.dev/spec/v1.0/)
- [OWASP SCVS](https://owasp.org/www-project-software-component-verification-standard/)
- [NIST Cybersecurity Framework](https://www.nist.gov/cyberframework)
- [CISA Software Security](https://www.cisa.gov/topics/cybersecurity-best-practices/software-security)
- [OpenSSF Best Practices](https://bestpractices.coreinfrastructure.org/)

---

<div align="center">

**These guardrails implement standards practically for AI agents** 🛡️

[⬆ Back to Main README](../README.md)

</div>
