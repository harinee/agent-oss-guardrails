# CI Actions and Build Tools

Specific guidance for CI/CD actions, workflows, and build tools.

## When to use this

Apply this overlay when working with GitHub Actions, GitLab CI, Jenkins plugins, or build automation tools.

## Instructions

### Treat as privileged dependencies

- treat CI actions and build tools as high-trust dependencies with elevated access
- recognize that CI tools often have access to:
  - source code
  - secrets and credentials
  - deployment systems
  - build artifacts

### Action selection

- prefer widely-used actions from verified publishers
- prefer official actions from GitHub, GitLab, or platform providers
- avoid actions from unknown or unverified publishers
- check action marketplace ratings and adoption

### Version pinning

- pin actions to specific versions or commit SHAs
- avoid using `@main` or `@master` branch references
- use full commit SHA for maximum security (e.g., `actions/checkout@a81bbb...`)
- avoid mutable tags that can change

### Action permissions

- review what permissions an action requires
- prefer actions with minimal permission requirements
- avoid actions that request broad repository access unnecessarily
- use workflow permissions to limit action capabilities

### Build tool selection

- prefer official build tools from framework authors
- avoid build plugins from unknown publishers
- verify build tool authenticity before use
- avoid build tools with unnecessary runtime dependencies

### Workflow security

- avoid exposing secrets in logs
- avoid using secrets in pull request workflows from forks
- use environment protection rules for sensitive deployments
- review workflow triggers carefully

### Third-party integrations

- verify third-party CI services before integrating
- review what access integrations require
- prefer minimal-access integrations
- document why specific integrations are needed
