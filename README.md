# 🛡️ Agent OSS Guardrails

> **Safe, composable instructions for AI agents managing open source dependencies**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](docs/contribution-guide.md)

---

## 🎯 What is this?

**Agent OSS Guardrails** provides reusable, modular instruction files that guide AI coding agents toward safer dependency selection practices for **supply chain risk reduction**.

**Why:** AI agents can introduce dependencies faster than humans can review them. These guardrails provide agent-readable constraints that encourage safer practices.

**Use cases:** AI coding agents (Cursor, Cline, GitHub Copilot, Aider, Windsurf), organizational policies, training guidelines

**Key characteristics:** Modular, ecosystem-specific, risk-adaptive, standards-aligned

**Reality check:** These are guidelines for AI agents, not security controls. They complement (not replace) SCA tools, SBOM, and code review. Effectiveness depends on agent capabilities.

[📖 Read why this exists](docs/why-this-exists.md)

---

## 🚀 Quick Start

### 1. Choose Your Baseline

```bash
# Most projects - balanced safety and flexibility
skills/foundational/oss-selection-baseline.skills.md

# Production/sensitive - strict controls
skills/foundational/oss-selection-strict.skills.md
```

### 2. Combine What You Need

```bash
# Node.js with autonomous agent
cat skills/foundational/oss-selection-baseline.skills.md \
    skills/overlays/capabilities/agent-can-install-packages.skills.md \
    skills/overlays/ecosystems/npm-node.skills.md \
    > .clinerules/oss-guardrails.md

# Or use pre-packaged combinations
cp packaged/baseline-general.skills.md .clinerules/oss-guardrails.md
```

[📖 Detailed selection guide](docs/how-to-choose.md)

---

## 📁 Repository Structure

```
skills/
├── foundational/          # baseline or strict
└── overlays/
    ├── capabilities/      # what agent can do
    ├── ecosystems/        # language-specific
    ├── artifact-types/    # CI/CD, scanners, MCP
    └── contexts/          # prototype, production, regulated

packaged/                  # ready-made combinations
examples/                  # usage examples
docs/                      # detailed guides
```

---

## 📖 Documentation

| Document | Purpose |
|----------|---------|
| [**Why This Exists**](docs/why-this-exists.md) | Supply chain risks & problem context |
| [**How to Choose**](docs/how-to-choose.md) | Decision guide with examples |
| [**Design Principles**](docs/design-principles.md) | 15 core principles |
| [**Mapping to Standards**](docs/mapping-to-standards.md) | SLSA, OWASP, NIST alignment |
| [**Contribution Guide**](docs/contribution-guide.md) | How to contribute |

---

## 🔧 Implementation

**For AI Agents:**
```bash
.clinerules/oss-guardrails.md           # Cline/Roo (project-level)
~/Documents/Cline/Rules/                # Cline (global)
.cursorrules                            # Cursor
.aider.conf.yml                         # Aider
.github/copilot-instructions.md         # GitHub Copilot
```

**For Organizations:**
- Artifact registry policies (Artifactory, Nexus)
- Policy-as-code (OPA, Kyverno)
- PR templates and pre-commit hooks

---

## 🤝 Contributing

Contributions welcome! See [Contribution Guide](docs/contribution-guide.md)

## 📄 License

MIT License - see [LICENSE](LICENSE)

---

<div align="center">

**Practical supply chain guidance for AI agents**

Built with lessons from [SLSA](https://slsa.dev/), [OWASP](https://owasp.org/), [NIST SSDF](https://csrc.nist.gov/Projects/ssdf)

[⬆ Back to Top](#-agent-oss-guardrails)

</div>
