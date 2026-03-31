# Why This Exists

## The challenge

AI agents increasingly influence dependency selection in software development. Traditional OSS governance guidance assumes human decision-making and careful evaluation at each step. However, AI agents operate differently:

### What agents can do

Agents can:
- introduce dependencies rapidly across multiple files
- select plugins, tools, and frameworks automatically
- modify lockfiles and dependency manifests
- introduce transitive dependencies without explicit consideration
- select new frameworks based on capability matching
- install tools dynamically during development
- add MCP servers and connectors
- introduce CI/CD actions and build tools
- pull container images

### Emerging risks

This creates new risks that traditional processes may not fully address:

**Dependency sprawl**: Agents can introduce many dependencies quickly, making the supply chain harder to audit and maintain.

**Malicious package introduction**: Automated selection may not detect typosquatting, compromised packages, or packages with malicious intent.

**Weak version pinning**: Agents may use flexible version ranges or latest tags, introducing unpredictability.

**Unsafe plugin ecosystems**: Browser extensions, editor plugins, and MCP servers may have broad access to source code and secrets.

**Hidden runtime dependencies**: Dynamic downloads, install scripts, and runtime fetching can bypass manifest visibility.

**Privileged tooling compromise**: Scanners, build tools, and CI actions often have elevated access to code, secrets, and deployment systems.

**Unclear maintenance status**: Agents may select packages that are abandoned, have single maintainers, or lack active security response.

**License incompatibility**: Rapid dependency addition may introduce licensing conflicts.

## The gap

Traditional OSS governance guidance is often:
- written for human audiences
- focused on policy and process
- not in a format agents can easily consume
- not specific to agent capabilities and behaviors

Teams using AI agents need:
- **Copy-pasteable instructions** that agents can follow consistently
- **Modular guidance** that adapts to different agent capabilities
- **Practical constraints** that can be applied during development
- **Ecosystem-specific guidance** for different languages and package managers
- **Context-aware rules** for different risk levels

## The goal

This repository provides reusable agent guardrails that:

✓ **Encourage minimal dependencies**: Only add what's truly needed

✓ **Encourage well-maintained packages**: Prefer packages with active maintenance and security response

✓ **Encourage version pinning**: Avoid unpredictable updates

✓ **Discourage unnecessary frameworks**: Avoid heavy frameworks for simple tasks

✓ **Ensure dependency visibility**: Keep dependencies in manifests and lockfiles

✓ **Discourage bypassing package managers**: Avoid curl-pipe-bash, git URLs, and dynamic downloads

✓ **Encourage review for privileged tools**: Treat CI actions, scanners, and connectors as high-trust dependencies

✓ **Support different contexts**: Adapt guidance for prototypes, production, and regulated environments

## What this does not replace

These guardrails complement but do not replace:

- **Software Composition Analysis (SCA)**: Automated vulnerability scanning and license detection
- **SBOM generation**: Creating comprehensive software bills of materials
- **Code review**: Human review of changes and architectural decisions
- **Legal license review**: Legal assessment of license compatibility
- **Vulnerability management**: Processes for responding to and remediating vulnerabilities
- **Security incident response**: Handling compromised dependencies or supply chain attacks

Think of these guardrails as a **first line of defense** that shapes agent behavior, reducing the likelihood of introducing problematic dependencies in the first place.
