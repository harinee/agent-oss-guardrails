# Design Principles

These principles guide the creation and maintenance of agent OSS guardrails.

## Core principles

### 1. Prefer minimal dependencies

**Why**: Every dependency is a potential attack surface and maintenance burden.

**Guidance**:
- Only add dependencies that provide clear value
- Avoid adding frameworks for simple tasks
- Avoid adding libraries for functionality already present
- Prefer standard library solutions when practical

### 2. Prefer well-maintained projects

**Why**: Maintained projects are more likely to receive security updates and bug fixes.

**Guidance**:
- Prefer projects with recent commits
- Prefer projects with responsive maintainers
- Prefer projects with active issue triage
- Avoid projects that appear abandoned

### 3. Prefer official sources

**Why**: Official packages and registries reduce the risk of malicious code.

**Guidance**:
- Use official package registries (npm, PyPI, Maven Central)
- Prefer official libraries from framework authors
- Avoid unofficial mirrors or forks unless necessary
- Verify publisher identity when possible

### 4. Pin versions

**Why**: Unpinned versions can introduce unexpected changes and vulnerabilities.

**Guidance**:
- Pin to specific versions, not ranges
- Avoid `latest` tags in containers
- Avoid `*` or `^` in package manifests where precision matters
- Update dependencies intentionally, not automatically

### 5. Avoid unnecessary frameworks

**Why**: Frameworks introduce significant code, complexity, and update burden.

**Guidance**:
- Use lightweight libraries for simple tasks
- Avoid heavy frameworks for single features
- Consider if existing frameworks can be extended
- Evaluate alternatives before adding a framework

### 6. Avoid hidden dependencies

**Why**: Hidden dependencies bypass auditing and visibility.

**Guidance**:
- Keep all dependencies in manifests
- Avoid dynamic runtime downloads
- Avoid install scripts that fetch additional code
- Ensure lockfiles are updated

### 7. Avoid dynamic code downloads

**Why**: Runtime code fetching bypasses review and scanning.

**Guidance**:
- Avoid `curl | bash` patterns
- Avoid dynamic imports from URLs
- Avoid eval or exec of fetched code
- Prefer static dependencies

### 8. Avoid unverified publishers

**Why**: Unknown publishers may be malicious or compromised.

**Guidance**:
- Check publisher reputation
- Verify maintainer identity where possible
- Be cautious of new packages from unknown publishers
- Prefer packages with verified publishers

### 9. Prefer discoverable dependencies

**Why**: All dependencies should be visible for auditing.

**Guidance**:
- Record dependencies in standard manifests
- Ensure lockfiles reflect all transitive dependencies
- Avoid bypassing package manager conventions
- Document non-standard dependency sources

### 10. Do not bypass lockfiles

**Why**: Lockfiles ensure reproducible builds and capture transitive dependencies.

**Guidance**:
- Never delete lockfiles to resolve issues
- Update lockfiles when dependencies change
- Commit lockfiles to version control
- Use lockfile validation in CI

### 11. Make changes reviewable

**Why**: Review catches issues that automated tools miss.

**Guidance**:
- Provide clear explanations for dependency additions
- Keep dependency changes in separate commits or PRs
- Flag high-impact changes explicitly
- Document rationale for unusual dependencies

### 12. Treat tools as dependencies

**Why**: Development tools have the same risks as runtime dependencies.

**Guidance**:
- Apply the same scrutiny to dev dependencies
- Pin tool versions
- Review tool permissions and access
- Document tool selection rationale

### 13. Treat plugins as dependencies

**Why**: Plugins often have elevated access to code and secrets.

**Guidance**:
- Apply dependency scrutiny to editor plugins
- Apply dependency scrutiny to browser extensions
- Review plugin permissions
- Prefer minimal-access plugins

### 14. Treat MCP servers as dependencies

**Why**: MCP servers and connectors can access code, execute commands, and handle secrets.

**Guidance**:
- Evaluate MCP server publishers
- Review MCP server permissions
- Pin MCP server versions
- Avoid unnecessary connectors

### 15. Prefer predictable supply chain behavior

**Why**: Unpredictability makes it harder to audit and secure the supply chain.

**Guidance**:
- Avoid auto-updates
- Avoid dynamic version resolution at runtime
- Prefer deterministic builds
- Test dependency updates before deploying

## Applying these principles

These principles inform the specific guidance in:
- Foundational skills files (baseline and strict)
- Capability overlays (what the agent can do)
- Ecosystem overlays (language-specific guidance)
- Artifact type overlays (CI, scanners, MCP servers)
- Context overlays (production, regulated, prototype)

When contributing new skills files, ensure they align with these principles while remaining practical for agent consumption.

## Balancing pragmatism

These principles are not absolute rules. There are valid exceptions:

- **Prototypes** may need faster iteration with relaxed constraints
- **Experimentation** may require testing new or unproven packages
- **Specialized needs** may require niche or single-maintainer packages
- **Legacy systems** may have dependencies that no longer meet current standards

The overlay system allows projects to adjust guardrails based on context while maintaining a clear baseline.
