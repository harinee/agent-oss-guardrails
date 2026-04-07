# 🤝 Contribution Guide

> Help make AI-assisted development safer for everyone

---

## 🚀 Quick Start

1. ⭐ Star the repository
2. 🍴 Fork the repository
3. 📖 Read [Design Principles](design-principles.md) and [Why This Exists](why-this-exists.md)
4. 💬 Check existing issues
5. 🗣️ Open a discussion for significant changes

---

## 🎯 Ways to Contribute

| Contribution | Impact |
|--------------|--------|
| 📝 Fix typos/improve clarity | High - Better docs help everyone |
| 🐛 Report issues or gaps | High - Identifies blind spots |
| 💡 Share real-world experiences | High - Validates/improves guidance |
| 🆕 Add ecosystem overlays | High - Expands coverage |
| 🔧 Create new overlay types | Very High - New capabilities |
| 📊 Add examples/case studies | High - Helps users apply guardrails |
| 🧪 Test with different agents | High - Validates effectiveness |

---

## 📋 Types of Contributions

### 1. New Overlay Files 🆕

**When to create:**
- Coverage gaps for capabilities, ecosystems, artifact types, or contexts
- Ecosystem-specific guidance not in existing files
- Addressing specific risk scenarios from real experience

**Examples needed:**
- 🦀 Rust / Cargo
- 💎 Ruby / Bundler
- 🔷 Go / Go modules
- 🌐 .NET / NuGet
- 🗄️ Database tools/ORMs

---

### 2. Updates to Existing Files ✏️

**When to update:**
- More effective phrasing for agents
- Missing scenarios in existing overlays
- Clarifying ambiguous guidance
- Incorporating lessons from incidents
- Agent behavior shows unclear guidance

---

### 3. New Packaged Combinations 📦

**When to create:**
- Common use case not covered
- Well-tested combination others benefit from
- Organizational stack used repeatedly

**Examples:** Go microservices, Ruby on Rails + CI/CD, Full-stack TypeScript, ML pipelines.

---

### 4. Documentation Improvements 📖

**High-impact contributions:**
- Real-world case studies
- Before/after examples
- Common pitfalls and solutions
- Integration guides for specific agents

---

## 📝 Writing Guidelines

### File Naming

```bash
✅ Good:
- npm-node.skills.md
- production.skills.md
- rust-cargo.skills.md

❌ Avoid:
- npm.md (missing .skills.md)
- Node-NPM.skills.md (use lowercase)
- node_npm.skills.md (use hyphens)
```

---

### Content Structure

```markdown
# {File Name}

> {Brief one-line description}

## When to use this

{1-2 sentences}

## Instructions

### {Category}
- instruction one
- instruction two

## Risk signals

- signal one → action
- signal two → action

## Examples

### ✅ Good patterns
### ❌ Patterns to avoid
```

---

### Language and Style

**✅ DO:**
- Use imperative voice: "prefer maintained packages"
- Be specific: "pin to 1.2.3 not ^1.2.0"
- Provide clear constraints: "avoid latest tags in production"

**❌ DON'T:**
- Passive voice: "packages should be maintained"
- Vague guidance: "use secure dependencies"
- Absolute without reason: "never use version ranges"
- Vendor-specific: "use Snyk to scan"

---

### One Variable Per File

| Category | Variable | Examples |
|----------|----------|----------|
| **Capabilities** | What agent can do | `agent-can-install-packages` |
| **Ecosystems** | Language/package manager | `npm-node`, `python-pip` |
| **Artifact Types** | Type of dependency | `ci-actions-build-tools` |
| **Contexts** | Risk level/environment | `production`, `regulated-sensitive` |

**If your file addresses multiple variables, split it.**

---

## 🧪 Testing Your Contribution

### Before Submitting

1. **Test with a real agent** (Cline, Cursor, Copilot, Aider)
2. **Observe:** Does the agent follow guidance? Clear instructions? Prevents risky patterns?
3. **Check conflicts:** Contradictions with existing files? Duplication?
4. **Verify completeness:** Main scenarios covered? Clear examples?

---

## 🔄 Contribution Process

### 1. Fork and Branch

```bash
git clone https://github.com/YOUR-USERNAME/agent-oss-guardrails.git
cd agent-oss-guardrails
git checkout -b add-rust-ecosystem-overlay
```

### 2. Make Focused Changes

- ✅ One overlay per PR
- ✅ One improvement type per PR
- ✅ Logical, complete changes

### 3. Test Thoroughly

Test with at least one AI agent and document results in PR.

### 4. Commit with Clear Messages

```bash
git commit -m "feat: add Rust/Cargo ecosystem overlay"
git commit -m "docs: improve how-to-choose examples"
git commit -m "fix: clarify version pinning in npm overlay"
```

### 5. Open Pull Request

**Use this template:**

```markdown
## What does this change?
{Brief description}

## What variable/category?
{Capability / Ecosystem / Artifact type / Context / Documentation}

## Why is this needed?
{Use case, gap, or problem}

## How was this tested?
**Agent used:** {Cline, Cursor, etc.}
**Scenarios tested:** {description}
**Observed behavior:** {what happened}

## Checklist
- [ ] Follows naming conventions
- [ ] Matches content structure
- [ ] Appropriate language/style
- [ ] Tested with AI agent
- [ ] No conflicts
- [ ] Docs updated if needed
```

---

## 🎯 What We're Looking For

**High-value contributions:**
1. Ecosystem overlays (Rust, Go, Ruby, .NET, PHP)
2. Real-world validation and case studies
3. Agent-specific insights and phrasing improvements
4. Regional/regulatory guidance (GDPR, industry-specific)

**We generally won't accept:**
- ❌ Vendor-specific guidance
- ❌ Promotional content
- ❌ Untested contributions
- ❌ Overly complex/verbose guidance
- ❌ Duplicate overlays without differentiation

---

## 📊 Review Process

**Reviewers check:**
1. Alignment with design principles
2. Clarity for agents
3. No duplication
4. Generic applicability
5. Proper formatting
6. Evidence of testing

**Timeline:**
- Simple fixes: 1-3 days
- New overlays: 1-2 weeks
- Significant changes: 2-4 weeks

---

## 💬 Getting Help

- 💡 General questions → [Discussions](https://github.com/harinee/agent-oss-guardrails/discussions)
- 🐛 Bugs → [Issues](https://github.com/harinee/agent-oss-guardrails/issues)
- 🤔 Unsure about contribution → Open Issue first

---

## 🌟 Recognition

Contributors are listed in contributors list, credited in release notes, and help the entire community!

Significant contributors may be invited as maintainers.

---

## 📜 Code of Conduct

**Standards:** Be respectful, welcome newcomers, constructive feedback, assume good intent.

**Not acceptable:** Harassment, discrimination, trolling, personal attacks, spam.

---

## 🎁 License

By contributing, your work is licensed under the **MIT License**.

---

<div align="center">

**Ready to contribute? We can't wait to see what you build!** 🚀

[⬆ Back to Main README](../README.md)

</div>
