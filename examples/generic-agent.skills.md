# Example: Generic Agent

This example shows a typical configuration for a general-purpose AI coding assistant working on a Node.js web application.

## Project context

- **Project type**: Node.js web application
- **Agent capabilities**: Can install packages, run limited shell commands
- **Risk level**: Standard development project
- **Environment**: Development/staging

## Selected skills files

```
skills/foundational/oss-selection-baseline.skills.md
+ skills/overlays/capabilities/agent-can-install-packages.skills.md
+ skills/overlays/capabilities/agent-can-run-shell.skills.md
+ skills/overlays/ecosystems/npm-node.skills.md
```

## Rationale

**Foundational baseline**: The project doesn't have strict security requirements, so the baseline provides appropriate guidance without being overly restrictive.

**Install packages**: The agent needs to add dependencies as part of feature development.

**Run shell**: The agent may need to run build commands, start development servers, etc.

**npm ecosystem**: Project-specific guidance for Node.js package management.

## Alternative: Use packaged file

Instead of combining individual files, you could use:

```
packaged/baseline-general.skills.md
+ skills/overlays/ecosystems/npm-node.skills.md
```

## Key behaviors

With this configuration, the agent will:
- ✓ Prefer well-maintained npm packages
- ✓ Pin dependency versions
- ✓ Explain dependency additions before installing
- ✓ Avoid `curl | bash` patterns
- ✓ Commit lockfiles (package-lock.json)
- ✓ Highlight risk signals (unmaintained packages, unknown publishers)

## What to add for stricter control

If the project moves to production:
```
+ skills/overlays/contexts/production.skills.md
```

If CI/CD is added:
```
+ skills/overlays/artifact-types/ci-actions-build-tools.skills.md
```

If the agent can open PRs:
```
+ skills/overlays/capabilities/agent-can-open-pr.skills.md
```
