# Scanners and Security Tools

Specific guidance for security scanners, static analysis tools, and security-focused tooling.

## When to use this

Apply this overlay when working with vulnerability scanners, SAST/DAST tools, or security analysis tools.

## Instructions

### Treat as high-trust tools

- recognize that security scanners often have privileged access to:
  - entire codebase
  - dependencies and manifests
  - security findings
  - potentially sensitive data

### Tool selection

- prefer reputable security tool publishers
- prefer tools from established security vendors
- avoid security tools from unknown publishers
- verify tool authenticity and reputation before use

### Tool permissions

- review what access security tools require
- avoid tools that request more access than necessary
- prefer read-only tools when possible
- be cautious of tools that modify code automatically

### Version management

- pin security tool versions
- avoid automatic tool updates without review
- test tool updates before deploying to production scanning
- document tool versions in CI configuration

### Data handling

- verify where scan results are sent
- avoid tools that transmit data to unknown destinations
- prefer tools that keep results local or in approved systems
- review tool privacy policies and data handling practices

### False positive management

- avoid automatically suppressing or ignoring findings without review
- document why specific findings are marked as false positives
- prefer manual review over automatic dismissal
- maintain audit trails for security decisions

### Integration security

- use secure methods to integrate tools (avoid exposing credentials)
- limit tool access to only what's needed for scanning
- use read-only tokens where possible
- rotate credentials for security tool integrations regularly
