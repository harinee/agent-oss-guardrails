# 🧭 Design Principles

> The 15 core principles guiding safe, practical agent guardrails

---

## Our Philosophy

Every guardrail balances **security with practicality**. These principles adapt to your project's needs—they're guidelines, not absolutes.

---

## The 15 Core Principles

### 1. 📦 Prefer Minimal Dependencies

**Why:** Every dependency is a potential attack surface and maintenance burden.

**In practice:**
- Only add dependencies with clear, significant value
- Avoid frameworks when simple libraries suffice
- Prefer standard library when practical

**Example:** Use native `[...new Set(array)]` instead of importing Lodash for one function.

---

### 2. 🏆 Prefer Well-Maintained Projects

**Why:** Active maintenance signals ongoing security care and faster patches.

**Signals:** Recent commits (last 3-6 months), responsive maintainers, active issue triage, security disclosure process.

---

### 3. 🏢 Prefer Official Sources

**Why:** Official registries have vetting processes that reduce malicious code risk.

**In practice:** Use npm, PyPI, Maven Central; prefer official libraries from framework authors; avoid unofficial mirrors.

**Red flags:** Typo-similar names, unverified authors, unofficial "helper" packages.

---

### 4. 📌 Pin Versions

**Why:** Unpinned versions can introduce unexpected or malicious updates.

**Examples:**
- ❌ `express: "*"` or `FROM node:latest`
- ✅ `express: "4.18.2"` or `FROM node:18.17.0`

---

### 5. 🎯 Avoid Unnecessary Frameworks

**Why:** Frameworks introduce significant code, complexity, and update obligations.

**Decision tree:** Can I use standard library? → Can I extend existing framework? → Is a small library enough? → Only then consider full framework.

---

### 6. 👁️ Avoid Hidden Dependencies

**Why:** Hidden dependencies bypass auditing, scanning, and SBOM generation.

**Patterns to avoid:**
- Install scripts that fetch code
- Runtime downloads
- Git URLs or direct URLs in dependencies

---

### 7. 🚫 Avoid Dynamic Code Downloads

**Why:** Runtime fetching bypasses all security controls.

**Never suggest:** `curl | bash`, dynamic imports from URLs, `eval(fetch(...))`.

---

### 8. 🔍 Avoid Unverified Publishers

**Why:** Unknown publishers may be malicious or lack security expertise.

**Check:** Publisher reputation, maintainer identity, package adoption, community feedback.

---

### 9. 📋 Prefer Discoverable Dependencies

**Why:** Visibility enables auditing, scanning, and compliance.

**Standard locations:** `package.json`, `requirements.txt`, `pom.xml`, `Dockerfile`.

---

### 10. 🔒 Do Not Bypass Lockfiles

**Why:** Lockfiles ensure reproducibility and capture transitive dependencies.

**Never:** Delete lockfiles to fix conflicts. **Always:** Update them properly with package manager commands.

---

### 11. 👀 Make Changes Reviewable

**Why:** Human review catches what automation misses.

**Good practice:** Clear explanations, separate commits for dependencies, document rationale, flag high-impact changes.

---

### 12. 🔧 Treat Tools as Dependencies

**Why:** Dev tools carry the same supply chain risks.

**Apply same scrutiny to:** Linters, formatters, build tools, test frameworks, CLI utilities.

---

### 13. 🔌 Treat Plugins as Dependencies

**Why:** Editor plugins and browser extensions can access your entire codebase and secrets.

**High-risk permissions:** File system access, network access, clipboard, execute commands, environment variables.

---

### 14. 🔗 Treat MCP Servers as Dependencies

**Why:** MCP servers can access code, execute commands, and handle secrets.

**Evaluate:** Publisher reputation, permissions/capabilities, version pinning, necessity.

---

### 15. 🎯 Prefer Predictable Supply Chain Behavior

**Why:** Unpredictability makes auditing and securing harder.

**Prioritize:** Deterministic builds, version pinning, no auto-updates, test before deploying.

---

## 🎨 Applying These Principles

### In Foundational Files
**Baseline** and **Strict** encode these at different strictness levels.

### In Overlay Files
Each overlay applies principles to specific contexts:
- **Capability overlays:** What the agent can do
- **Ecosystem overlays:** Language-specific guidance
- **Artifact type overlays:** CI/CD, scanners, MCP
- **Context overlays:** Production, regulated, prototype

---

## ⚖️ Balancing Pragmatism

**Valid exceptions exist:**

| Context | Flexibility |
|---------|------------|
| 🧪 Prototypes | Faster iteration, relaxed constraints |
| 🔬 Experimentation | Testing unproven packages allowed |
| 🎯 Specialized needs | Niche packages may be necessary |
| 🏛️ Legacy systems | Existing deps may not meet standards |

The overlay system lets you adapt while maintaining clear baselines.

---

## 🔄 Principles in Practice

**When adding a dependency, check:**

1. ✅ Do I really need this? (Minimal)
2. ✅ Recent commits? Active issues? (Well-maintained)
3. ✅ Official registry? Verified publisher? (Official)
4. ✅ Exact version specified? (Pinned)
5. ✅ Is a library enough? (Not a framework)
6. ✅ In manifest and lockfile? (Discoverable)
7. ✅ Static dependency? (Not dynamic)
8. ✅ Known maintainer? (Verified publisher)
9. ✅ Clear documentation? (Reviewable)

**All pass ✅ → Add it**  
**Any fail ⚠️ → Reconsider or document exception**

---

<div align="center">

**These principles create a foundation for safer AI-assisted development** 🛡️

[⬆ Back to Main README](../README.md)

</div>
