# Agent Can Use Tools or MCP

Additional guidance when the agent can use tools, plugins, or MCP servers.

## When to use this

Apply this overlay when your agent can install or use MCP servers, tool connectors, plugins, or extensions.

## Instructions

### Treat tools as dependencies

- apply the same scrutiny to tools and MCP servers as you would to code dependencies
- verify publisher reputation before using new tools
- check tool permissions and access requirements
- prefer tools from verified or well-known publishers

### Permission awareness

- avoid tools that request broad permissions unnecessarily
- prefer minimal-access tools that only request what they need
- highlight when a tool requires access to:
  - source code
  - environment variables or secrets
  - file system write access
  - network access
  - command execution privileges

### Tool selection

- avoid installing unnecessary connectors or tools
- prefer official tools from framework or platform authors
- avoid experimental or unverified tools in production contexts
- explain why a specific tool is needed before installing

### MCP server considerations

- treat MCP servers as privileged dependencies with code and secret access
- verify MCP server publishers before installation
- prefer minimal-scope MCP servers
- avoid MCP servers with unclear functionality
- document what MCP servers are installed and why

### Version management

- pin tool and MCP server versions
- avoid auto-updating tools without review
- document tool versions in project configuration
- update tools intentionally, not automatically

### Discovery and installation

- avoid dynamic tool discovery without explanation
- explain what a tool does before using it for the first time
- avoid installing multiple tools that provide the same functionality
- prefer tools that are already configured in the project
