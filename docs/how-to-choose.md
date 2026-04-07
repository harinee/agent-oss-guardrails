# 🗺️ How to Choose

> A practical guide to selecting the perfect combination of guardrails for your project

---

## 🎯 Quick Decision

1. **Production system?** → Use **strict** foundation
2. **Prototype/experiment?** → Use **baseline** foundation
3. **What language?** → Add ecosystem overlay
4. **Can agent install packages?** → Add capability overlays
5. **Risk tolerance?** → Add context overlay

---

## 📋 5-Step Selection Process

### Step 1: Choose Your Foundation 🏗️

Pick **exactly one** foundation:

| Foundation | Best For | Files |
|-----------|----------|-------|
| ⚖️ **Baseline** | General dev, internal tools, prototypes, lower-risk apps | `oss-selection-baseline.skills.md` |
| 🔒 **Strict** | Production, sensitive data, regulated industries, customer-facing | `oss-selection-strict.skills.md` |

**💡 Tip:** Start with **baseline**, upgrade to **strict** if needed.

---

### Step 2: Add Capability Overlays 🎯

Add based on what your agent can do:

| If Agent Can... | Add Overlay |
|----------------|-------------|
| 📦 Install packages | `agent-can-install-packages` |
| 💻 Run shell commands | `agent-can-run-shell` |
| 🔧 Use tools/MCP | `agent-can-use-tools-or-mcp` |
| 🔀 Create PRs | `agent-can-open-pr` |

**Example:**
- Low autonomy (suggests only) → No overlays
- Medium autonomy (installs) → `+ agent-can-install-packages`
- High autonomy (all) → Add all applicable overlays

---

### Step 3: Add Ecosystem Overlays 🎨

Add for each ecosystem you use (can include multiple):

| Project Uses | Add Overlay |
|-------------|-------------|
| 🟢 Node.js / npm | `npm-node` |
| 🐍 Python / pip | `python-pip` |
| ☕ Java / Maven | `java-maven-gradle` |
| 🐳 Docker | `container-images` |

---

### Step 4: Add Artifact Type Overlays 🔧

Add for specialized dependency types:

| Uses | Add Overlay |
|------|-------------|
| ⚙️ CI/CD Actions | `ci-actions-build-tools` |
| 🔍 Scanners/Security Tools | `scanners-security-tools` |
| 🔗 MCP Servers | `mcp-servers-connectors` |

---

### Step 5: Add Context Overlay 🎚️

Choose **one** based on risk profile:

| Context | When to Use | File |
|---------|------------|------|
| 🧪 **Prototype** | POCs, learning, hackathons, experiments | `prototype-low-risk` |
| 🏗️ **Production** | Live apps, customer-facing, revenue-generating | `production` |
| 🔒 **Regulated** | Healthcare, finance, government, compliance | `regulated-sensitive` |

---

## 💡 Real-World Examples

### Example 1: Simple Web App 🌐

**Scenario:** Personal portfolio with React

```bash
cat skills/foundational/oss-selection-baseline.skills.md \
    skills/overlays/capabilities/agent-can-install-packages.skills.md \
    skills/overlays/ecosystems/npm-node.skills.md \
    > .clinerules/oss-guardrails.md
```

---

### Example 2: Production Microservice 🚀

**Scenario:** FastAPI backend, Docker, CI/CD, production traffic

```bash
cat skills/foundational/oss-selection-strict.skills.md \
    skills/overlays/capabilities/agent-can-install-packages.skills.md \
    skills/overlays/capabilities/agent-can-open-pr.skills.md \
    skills/overlays/ecosystems/python-pip.skills.md \
    skills/overlays/ecosystems/container-images.skills.md \
    skills/overlays/artifact-types/ci-actions-build-tools.skills.md \
    skills/overlays/contexts/production.skills.md \
    > .clinerules/oss-guardrails.md

# Or use pre-packaged
cp packaged/python-sensitive-repo.skills.md .clinerules/oss-guardrails.md
```

---

### Example 3: High-Autonomy Agent 🤖

**Scenario:** Agent with broad permissions

```bash
cat skills/foundational/oss-selection-strict.skills.md \
    skills/overlays/capabilities/agent-can-install-packages.skills.md \
    skills/overlays/capabilities/agent-can-run-shell.skills.md \
    skills/overlays/capabilities/agent-can-use-tools-or-mcp.skills.md \
    skills/overlays/ecosystems/npm-node.skills.md \
    skills/overlays/artifact-types/mcp-servers-connectors.skills.md \
    > .clinerules/oss-guardrails.md

# Or use pre-packaged
cp packaged/strict-agent-high-autonomy.skills.md .clinerules/oss-guardrails.md
```

---

### Example 4: Healthcare Compliance 🏥

**Scenario:** HIPAA-compliant Java system

```bash
cat skills/foundational/oss-selection-strict.skills.md \
    skills/overlays/capabilities/agent-can-install-packages.skills.md \
    skills/overlays/ecosystems/java-maven-gradle.skills.md \
    skills/overlays/artifact-types/scanners-security-tools.skills.md \
    skills/overlays/contexts/regulated-sensitive.skills.md \
    > .clinerules/oss-guardrails.md
```

---

## 📦 Pre-Packaged Combinations

| Package | Best For |
|---------|----------|
| 🎯 **baseline-general** | Most common use case |
| 🔒 **strict-agent-high-autonomy** | Powerful agents needing constraints |
| 🐍 **python-sensitive-repo** | Python production projects |
| 🟢 **npm-high-autonomy** | Node.js with autonomous agent |

**Usage:**
```bash
cp packaged/[package-name].skills.md .clinerules/oss-guardrails.md
```

---

## 🔧 How to Apply

### Project-Level (Recommended)

```bash
.clinerules/oss-guardrails.md           # Cline/Roo
.cursorrules                            # Cursor
.aider.conf.yml                         # Aider
.github/copilot-instructions.md         # GitHub Copilot
```

### Global (All Projects)

```bash
~/Documents/Cline/Rules/oss-guardrails.md    # Cline
~/.cursor/rules/oss-guardrails.md            # Cursor
```

---

## 📊 Decision Matrix

|  | Prototype | Internal | Production | Regulated |
|---|:-:|:-:|:-:|:-:|
| **Foundation** | Baseline | Baseline | **Strict** | **Strict** |
| **Ecosystem** | ✓ | ✓ | ✓ | ✓ |
| **Capabilities** | ✓ | ✓ | ✓ | ✓ |
| **Artifact Types** | Optional | Optional | ✓ | ✓ |
| **Context** | prototype | (none) | production | regulated |

---

## ⏰ When to Update

| Trigger | Action |
|---------|--------|
| 🚀 Moving to production | Upgrade baseline → strict |
| 🤖 Agent capabilities change | Add/remove capability overlays |
| 🆕 New dependency types | Add artifact type overlays |
| 🚨 Supply chain incident | Review and strengthen |
| 📈 Project risk increases | Add stricter context |

---

## 🆘 Still Need Help?

**Start simple:**
```bash
packaged/baseline-general.skills.md
```

Observe for a week, then adjust based on agent behavior and your risk tolerance.

---

<div align="center">

**Start simple, observe, iterate. Add more guardrails later!** 🛡️

[⬆ Back to Main README](../README.md)

</div>
