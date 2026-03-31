# MCP Servers and Connectors

Specific guidance for MCP (Model Context Protocol) servers and connectors.

## When to use this

Apply this overlay when working with MCP servers, connectors, or tool integrations.

## Instructions

### Treat as dependencies

- treat MCP servers as dependencies with the same scrutiny as code libraries
- recognize that MCP servers can have broad access to:
  - source code and files
  - command execution
  - environment variables and secrets
  - external APIs and services

### Server selection

- prefer MCP servers from verified or well-known publishers
- avoid MCP servers from unknown or unverified sources
- check server documentation and reputation before installing
- prefer official servers from framework or platform authors

### Permission awareness

- review what permissions an MCP server requests
- avoid servers that request unnecessarily broad access
- prefer minimal-scope servers that only access what they need
- highlight when a server requires:
  - file system write access
  - command execution privileges
  - network access
  - access to secrets or environment variables

### Version management

- pin MCP server versions in configuration
- avoid auto-updating MCP servers without review
- document which MCP servers are installed and why
- test MCP server updates before deploying

### Connector evaluation

- avoid installing connectors for services not actively used
- prefer official connectors from service providers
- review connector data handling and privacy policies
- document what external services connectors access

### Configuration security

- avoid storing credentials in MCP server configuration
- use secure credential management for connectors
- limit connector access to minimum required scope
- review and rotate credentials for connectors

### Unnecessary installations

- avoid installing MCP servers "just in case"
- remove unused MCP servers and connectors
- prefer built-in capabilities over external servers when possible
- evaluate whether a connector is truly needed before installing
