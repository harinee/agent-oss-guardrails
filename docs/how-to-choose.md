# How to Choose

This guide helps you select the right combination of skills files for your project and agent configuration.

## Decision tree

### Step 1: Start with a foundation

Every project should begin with one foundational skills file:

**For most projects:**
```
skills/foundational/oss-selection-baseline.skills.md
```

**For sensitive or production-critical projects:**
```
skills/foundational/oss-selection-strict.skills.md
```

### Step 2: Add capability overlays

Add overlays based on what your agent can do:

| If your agent can... | Add this overlay |
|---------------------|------------------|
| Install packages directly | `skills/overlays/capabilities/agent-can-install-packages.skills.md` |
| Run shell commands | `skills/overlays/capabilities/agent-can-run-shell.skills.md` |
| Use tools or MCP servers | `skills/overlays/capabilities/agent-can-use-tools-or-mcp.skills.md` |
| Create or update PRs automatically | `skills/overlays/capabilities/agent-can-open-pr.skills.md` |

### Step 3: Add ecosystem overlays

Add overlays based on your project's language and package manager:

| Ecosystem | Add this overlay |
|-----------|------------------|
| Node.js / npm / yarn | `skills/overlays/ecosystems/npm-node.skills.md` |
| Python / pip / poetry | `skills/overlays/ecosystems/python-pip.skills.md` |
| Java / Maven / Gradle | `skills/overlays/ecosystems/java-maven-gradle.skills.md` |
| Container images | `skills/overlays/ecosystems/container-images.skills.md` |

### Step 4: Add artifact type overlays

Add overlays based on the types of dependencies and tools your project uses:

| Artifact type | Add this overlay |
|--------------|------------------|
| CI/CD actions and build tools | `skills/overlays/artifact-types/ci-actions-build-tools.skills.md` |
| Security scanners and analysis tools | `skills/overlays/artifact-types/scanners-security-tools.skills.md` |
| MCP servers and connectors | `skills/overlays/artifact-types/mcp-servers-connectors.skills.md` |

### Step 5: Add context overlays

Add overlays based on your project's risk profile:

| Context | Add this overlay |
|---------|------------------|
| Prototype or low-risk experimentation | `skills/overlays/contexts/prototype-low-risk.skills.md` |
| Production systems | `skills/overlays/contexts/production.skills.md` |
| Regulated or sensitive environments | `skills/overlays/contexts/regulated-sensitive.skills.md` |

## Example combinations

### Example 1: Basic Node.js web application

```
skills/foundational/oss-selection-baseline.skills.md
+ skills/overlays/capabilities/agent-can-install-packages.skills.md
+ skills/overlays/ecosystems/npm-node.skills.md
```

### Example 2: Python data science prototype

```
skills/foundational/oss-selection-baseline.skills.md
+ skills/overlays/capabilities/agent-can-install-packages.skills.md
+ skills/overlays/ecosystems/python-pip.skills.md
+ skills/overlays/contexts/prototype-low-risk.skills.md
```

### Example 3: Production microservice with CI/CD

```
skills/foundational/oss-selection-strict.skills.md
+ skills/overlays/capabilities/agent-can-install-packages.skills.md
+ skills/overlays/capabilities/agent-can-open-pr.skills.md
+ skills/overlays/ecosystems/python-pip.skills.md
+ skills/overlays/ecosystems/container-images.skills.md
+ skills/overlays/artifact-types/ci-actions-build-tools.skills.md
+ skills/overlays/contexts/production.skills.md
```

### Example 4: Regulated environment with high autonomy agent

```
skills/foundational/oss-selection-strict.skills.md
+ skills/overlays/capabilities/agent-can-install-packages.skills.md
+ skills/overlays/capabilities/agent-can-run-shell.skills.md
+ skills/overlays/capabilities/agent-can-use-tools-or-mcp.skills.md
+ skills/overlays/capabilities/agent-can-open-pr.skills.md
+ skills/overlays/ecosystems/java-maven-gradle.skills.md
+ skills/overlays/artifact-types/scanners-security-tools.skills.md
+ skills/overlays/contexts/regulated-sensitive.skills.md
```

## Using packaged combinations

If you don't want to combine files manually, use pre-packaged combinations:

- `packaged/baseline-general.skills.md` - General purpose baseline
- `packaged/strict-agent-high-autonomy.skills.md` - For highly autonomous agents
- `packaged/python-sensitive-repo.skills.md` - Python in sensitive environments
- `packaged/npm-high-autonomy.skills.md` - Node.js with autonomous agent

## How to apply these files

Most AI agents and coding assistants support a `skills.md` or similar configuration file. Common approaches:

1. **Project-level**: Place the combined content in `.clinerules/`, `.cursorrules`, or a similar project configuration file
2. **Agent configuration**: Add the content to your agent's system prompt or instructions
3. **Multiple files**: Some systems support including multiple skill files - use the overlay structure directly

## When to update

Review and update your skills configuration when:

- Agent capabilities change (new permissions or tools)
- Project risk profile changes (moving to production)
- New dependency types are introduced (adding containers, CI/CD)
- Supply chain incidents occur (update guidance based on lessons learned)
- Ecosystem best practices evolve

## Need help?

If you're unsure which combination to use, start with the **baseline-general** packaged file and adjust based on observed agent behavior and your team's risk tolerance.
