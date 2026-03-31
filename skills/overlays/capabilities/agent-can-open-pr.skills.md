# Agent Can Open Pull Requests

Additional guidance when the agent can create or update pull requests automatically.

## When to use this

Apply this overlay when your agent can open PRs or commit changes automatically.

## Instructions

### PR descriptions

- include clear explanation of dependency changes in PR descriptions
- document why each new dependency was added
- list alternatives that were considered
- highlight any risk signals or concerns

### Dependency changes visibility

- ensure dependency additions are clearly visible in the PR
- include both manifest and lockfile changes
- avoid bundling large dependency changes with unrelated code changes
- separate dependency updates into focused commits

### High-impact changes

- flag when adding new foundational frameworks
- flag when adding dependencies with elevated permissions
- flag when introducing new package ecosystems
- flag when adding tools with code execution capabilities

### PR scope

- avoid adding many dependencies in a single PR without justification
- prefer incremental dependency additions
- keep dependency changes separate from feature implementation where practical
- make it easy for reviewers to assess dependency changes

### Documentation in commits

- write clear commit messages explaining dependency additions
- document version selections and why specific versions were chosen
- note if a dependency introduces transitive dependencies
- explain any deviation from standard patterns

### Review signals

Add labels or notes in PRs when:
- introducing dependencies from new or unverified publishers
- adding tools with privileged access
- introducing new frameworks or significant complexity
- updating many dependencies at once
- making changes to lockfiles
