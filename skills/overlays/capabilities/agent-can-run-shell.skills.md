# Agent Can Run Shell

Additional guidance when the agent has permission to execute shell commands.

## When to use this

Apply this overlay when your agent can execute arbitrary shell commands.

## Instructions

### Avoid risky patterns

- avoid `curl | bash` or `wget | sh` patterns
- avoid piping URLs directly to shell interpreters
- avoid executing remote scripts without review
- avoid downloading and executing binaries from arbitrary URLs

### Package installation

- prefer package manager commands over manual downloads
- use official package managers (apt, brew, yum) for system packages
- avoid compiling from source unless necessary
- verify checksums or signatures when downloading files

### System modifications

- avoid modifying system configuration unnecessarily
- avoid changing permissions on system files
- avoid installing system-wide dependencies unless explicitly required
- prefer user-level or project-level installations

### Script execution

- explain what shell commands will do before executing
- avoid executing scripts from untrusted sources
- prefer reading and understanding scripts before running them
- avoid using eval or exec with unsanitized input

### Download behavior

- download from official sources and registries
- verify file integrity after download (checksums, signatures)
- avoid downloading from arbitrary or shortened URLs
- save downloads to project directories, not system locations

### Environment changes

- avoid permanently modifying shell environment (bashrc, profile, etc.)
- prefer project-specific environment configuration
- document any environment changes
- avoid setting global environment variables unnecessarily
