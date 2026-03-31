# Contribution Guide

Thank you for considering contributing to Agent OSS Guardrails! This guide will help you create contributions that align with the project's goals and design principles.

## Before contributing

1. **Review existing files**: Check if similar guidance already exists
2. **Read design principles**: Understand the project's [design principles](design-principles.md)
3. **Check the issue tracker**: See if someone else is working on something similar
4. **Open a discussion**: For significant changes, open an issue first to discuss the approach

## Types of contributions

### New overlay files

Create new overlay files when:
- You've identified a new capability, ecosystem, artifact type, or context not yet covered
- You have ecosystem-specific guidance that doesn't fit existing files
- You need to address a specific risk scenario

### Updates to existing files

Update existing files when:
- You've found more effective phrasing for agent consumption
- You've identified missing scenarios in an existing overlay
- You need to clarify ambiguous guidance
- You're incorporating lessons from supply chain incidents

### New packaged combinations

Create new packaged combinations when:
- You've identified a common use case not covered by existing packages
- You have a well-tested combination that others might benefit from

### Documentation improvements

Improve documentation when:
- You've found unclear or missing guidance
- You can provide better examples
- You can clarify decision trees or mappings

## File naming conventions

Follow these naming conventions:

**Overlay files**: `{descriptive-name}.skills.md`
- Use lowercase with hyphens
- Be specific but concise
- Examples: `npm-node.skills.md`, `production.skills.md`

**Packaged files**: `{use-case}.skills.md`
- Describe the target use case
- Examples: `python-sensitive-repo.skills.md`

## Writing skills instructions

### Principles for writing

1. **Be concise**: Agents process instructions more reliably when they're clear and brief
2. **Be explicit**: Avoid ambiguity - specify exactly what behavior you want
3. **Be actionable**: Provide guidance the agent can act on
4. **Be generic**: Avoid company-specific or vendor-specific references
5. **Be modular**: Each instruction should work independently and compose well

### Format guidelines

Use this structure for skills files:

```markdown
# {File Name}

{Brief description of what this overlay addresses}

## When to use this

{1-2 sentences describing when to include this overlay}

## Instructions

### {Category 1}

- instruction one
- instruction two
- instruction three

### {Category 2}

- instruction one
- instruction two

## Risk signals

If the agent encounters these signals, it should:
- signal one → action
- signal two → action
```

### Language style

**DO**:
- Use imperative voice: "prefer maintained packages"
- Be specific: "pin to specific versions" not "use good versions"
- Provide clear constraints: "avoid packages with no commits in 12+ months"

**DON'T**:
- Use passive voice: "packages should be maintained"
- Be vague: "use secure dependencies"
- Use judgmental language: "never", "always", "must" (unless truly absolute)
- Reference specific companies or products

### Examples

**Good**:
```markdown
- prefer packages with commits in the last 6 months
- avoid packages from unverified publishers
- pin to specific semantic versions (e.g., 1.2.3 not ^1.2.0)
```

**Not ideal**:
```markdown
- use maintained packages
- be careful with dependencies
- always use the latest version
```

## What variable does your file address?

Each overlay file should address ONE primary variable:

| Category | Variable |
|----------|----------|
| Capabilities | What the agent can do (install, execute, open PRs) |
| Ecosystems | Language/package manager context |
| Artifact types | Type of dependency (CI action, scanner, MCP server) |
| Contexts | Risk level (prototype, production, regulated) |

If your file addresses multiple variables, consider splitting it into multiple overlays.

## Avoiding duplication

Before creating new guidance:

1. **Check foundational files**: Is this guidance already in baseline or strict?
2. **Check existing overlays**: Does another overlay already address this?
3. **Consider composition**: Can existing files be combined instead?

If you find duplication:
- Contribute by refactoring to remove it
- Move common guidance to foundational files
- Keep overlays focused on the delta they provide

## Testing your contribution

Before submitting:

1. **Test with an agent**: Use your skills file with a real AI agent and observe behavior
2. **Check for conflicts**: Ensure your guidance doesn't contradict other files
3. **Verify composition**: Test your overlay combined with baseline and other overlays
4. **Document use cases**: Note which scenarios benefit from your guidance

## Submitting contributions

### Pull request process

1. **Fork the repository**
2. **Create a feature branch**: `git checkout -b add-rust-ecosystem-overlay`
3. **Make your changes**: Follow the guidelines in this document
4. **Test thoroughly**: Ensure your changes work as intended
5. **Commit with clear messages**: Use conventional commit format
6. **Open a pull request**: Provide a clear description of your changes

### Pull request template

Include in your PR description:

```markdown
## What does this change?

{Brief description}

## What variable does it address?

{Capability / Ecosystem / Artifact type / Context}

## Why is this needed?

{Use case or gap it fills}

## How was this tested?

{Agent used, scenarios tested, observed behavior}

## Does it duplicate existing guidance?

{Yes/No - if yes, explain why it's necessary}

## Related issues

{Link to relevant issues or discussions}
```

### Review process

Contributions will be reviewed for:
- Alignment with design principles
- Clarity for agent consumption
- Absence of duplication
- Generic applicability
- Proper formatting

## Contribution ideas

Looking for ways to contribute? Consider:

- **New ecosystem overlays**: Rust, Go, Ruby, PHP, .NET
- **New artifact types**: Database tools, monitoring agents, deployment tools
- **Regional considerations**: Specific guidance for different regulatory regions
- **Incident response**: Update guidance based on recent supply chain incidents
- **Agent feedback**: Improve phrasing based on observed agent behavior
- **Examples**: More real-world usage examples
- **Testing**: Tools or scripts to validate skills files

## Code of conduct

- Be respectful and inclusive
- Focus on constructive feedback
- Assume good intent
- Help newcomers
- Keep discussions professional

## Questions?

- Open an issue for questions about contributing
- Use discussions for broader topics
- Tag maintainers for urgent security-related matters

## License

By contributing, you agree that your contributions will be licensed under the same MIT License that covers the project.

---

Thank you for helping make AI-assisted development safer! 🛡️
