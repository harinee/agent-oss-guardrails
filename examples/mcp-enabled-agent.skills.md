# Example: MCP-Enabled Agent

This example shows configuration for an agent that can use MCP servers and tools.

## Project context

- **Project type**: Python data analysis application
- **Agent capabilities**: Can install packages, use MCP servers and tools
- **Risk level**: Internal tooling, moderate sensitivity
- **Environment**: Development with access to internal data

## Selected skills files

```
skills/foundational/oss-selection-baseline.skills.md
+ skills/overlays/capabilities/agent-can-install-packages.skills.md
+ skills/overlays/capabilities/agent-can-use-tools-or-mcp.skills.md
+ skills/overlays/ecosystems/python-pip.skills.md
+ skills/overlays/artifact-types/mcp-servers-connectors.skills.md
```

## Rationale

**Foundational baseline**: Standard guidance for dependency selection.

**Install packages**: Agent needs to add Python libraries for data analysis tasks.

**Use tools or MCP**: Agent can leverage MCP servers for enhanced capabilities (database access, API connectors, etc.).

**Python ecosystem**: Project-specific guidance for pip and Python packages.

**MCP servers**: Specific guidance for evaluating and using MCP servers since they have access to code and potentially sensitive data.

## Key behaviors

With this configuration, the agent will:
- ✓ Treat MCP servers as dependencies requiring scrutiny
- ✓ Verify MCP server publishers before installation
- ✓ Review MCP server permissions (file access, command execution, etc.)
- ✓ Pin MCP server versions in configuration
- ✓ Document which MCP servers are installed and why
- ✓ Prefer minimal-scope MCP servers
- ✓ Follow Python best practices (virtual environments, pinned versions)

## Example scenarios

**Scenario 1: Agent wants to add database connector**

Agent behavior:
1. Explains why database access is needed
2. Identifies official database MCP server or connector
3. Reviews permissions required (read/write access, connection credentials)
4. Highlights if connector requires broad permissions
5. Waits for confirmation before installing
6. Pins connector version in configuration
7. Documents the connector purpose

**Scenario 2: Agent wants to install analysis library**

Agent behavior:
1. Checks if library is well-maintained on PyPI
2. Verifies package authenticity
3. Installs specific version (pip install pandas==2.0.3)
4. Updates requirements.txt
5. Commits requirements.txt changes

## What to add for production use

If this tool processes production data:
```
+ skills/overlays/contexts/production.skills.md
```

If this tool handles regulated data:
```
+ skills/overlays/contexts/regulated-sensitive.skills.md
```

## Security considerations

Because this agent:
- Has access to internal data through MCP servers
- Can install packages that process sensitive data
- Uses connectors that may access databases or APIs

The MCP overlay ensures:
- MCP servers are reviewed before use
- Permissions are appropriate and minimal
- Server versions are pinned and documented
- Unused servers are removed
