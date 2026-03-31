# Agent OSS Guardrails

Reusable skills.md instructions for safer open source dependency selection and tool usage in AI-assisted software development.

These files help teams guide coding assistants and agents when they:
- suggest libraries or frameworks
- install packages
- modify dependencies
- use MCP servers or plugins
- introduce CI/CD tools or actions
- pull container images
- introduce scanners or developer tooling

## Why this exists

General OSS governance guidance exists, but teams using AI agents often need copy-pasteable instructions that constrain agent behavior consistently.

Recent supply chain incidents have shown that:
- popular packages can be compromised temporarily
- automated dependency updates can introduce risk
- tools and plugins may have privileged access to source code and secrets
- agents can unintentionally introduce unsafe or unnecessary dependencies

This repository helps translate general OSS hygiene principles into practical agent instructions.

## What this repository DOES

- provides reusable skills.md blocks
- helps teams choose appropriate guardrails
- supports different agent capabilities and environments
- encourages safer dependency practices

## What this repository DOES NOT replace

- Software Composition Analysis (SCA)
- SBOM generation
- code review
- legal license review
- vulnerability management
- security incident processes

## Quick start

Most teams can start with:

```
skills/foundational/oss-selection-baseline.skills.md
```

Then add overlays based on:

- agent capability
- ecosystem
- risk level
- artifact type

See [docs/how-to-choose.md](docs/how-to-choose.md) for guidance.

## Documentation

- [Why this exists](docs/why-this-exists.md)
- [How to choose](docs/how-to-choose.md)
- [Design principles](docs/design-principles.md)
- [Mapping to standards](docs/mapping-to-standards.md)
- [Contribution guide](docs/contribution-guide.md)

## Repository structure

```
agent-oss-guardrails/
├── skills/
│   ├── foundational/          # Baseline and strict guardrails
│   ├── overlays/
│   │   ├── capabilities/      # Based on what the agent can do
│   │   ├── ecosystems/        # Language/package manager specific
│   │   ├── artifact-types/    # CI, scanners, MCP servers, etc.
│   │   └── contexts/          # Production, prototype, regulated
├── packaged/                  # Pre-combined skill sets
├── examples/                  # Usage examples
└── docs/                      # Documentation
```

## License

MIT License - see [LICENSE](LICENSE) for details.
