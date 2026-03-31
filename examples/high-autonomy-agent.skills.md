# Example: High Autonomy Agent

This example shows configuration for a highly autonomous agent in a production environment.

## Project context

- **Project type**: Production microservice (Java)
- **Agent capabilities**: Full autonomy - install packages, run shell, use tools, open PRs
- **Risk level**: High - customer-facing production system
- **Environment**: Production with CI/CD pipeline

## Selected skills files

```
skills/foundational/oss-selection-strict.skills.md
+ skills/overlays/capabilities/agent-can-install-packages.skills.md
+ skills/overlays/capabilities/agent-can-run-shell.skills.md
+ skills/overlays/capabilities/agent-can-use-tools-or-mcp.skills.md
+ skills/overlays/capabilities/agent-can-open-pr.skills.md
+ skills/overlays/ecosystems/java-maven-gradle.skills.md
+ skills/overlays/ecosystems/container-images.skills.md
+ skills/overlays/artifact-types/ci-actions-build-tools.skills.md
+ skills/overlays/artifact-types/scanners-security-tools.skills.md
+ skills/overlays/contexts/production.skills.md
```

## Rationale

**Strict foundation**: High-autonomy agent in production requires stricter baseline controls.

**All capability overlays**: Agent has full autonomy, so all capability guardrails apply.

**Multiple ecosystems**: Java application deployed in containers, so both overlays needed.

**Artifact types**: CI/CD pipeline and security scanning tools require specific guidance.

**Production context**: Additional production-specific controls for stability and rollback.

## Alternative: Use packaged file

A simpler approach:

```
packaged/strict-agent-high-autonomy.skills.md
+ skills/overlays/ecosystems/java-maven-gradle.skills.md
+ skills/overlays/ecosystems/container-images.skills.md
+ skills/overlays/artifact-types/ci-actions-build-tools.skills.md
+ skills/overlays/artifact-types/scanners-security-tools.skills.md
```

## Key behaviors

With this configuration, the agent will:

**Dependency selection:**
- ✗ Avoid newly published packages (< 6 months)
- ✗ Avoid packages from unverified publishers
- ✗ Avoid single-maintainer packages in critical paths
- ✓ Require explicit approval for new frameworks
- ✓ Pin exact versions with no flexibility

**Installation:**
- ✓ Explain dependency additions before installing
- ✓ Highlight all risk signals
- ✓ Wait for confirmation on any risky changes
- ✗ Forbid `curl | bash` patterns
- ✗ Forbid dynamic downloads

**PRs:**
- ✓ Include detailed dependency rationale in PR descriptions
- ✓ Flag high-impact changes (frameworks, privileged tools)
- ✓ Keep dependency changes in focused PRs
- ✓ Document alternatives considered

**CI/CD:**
- ✓ Pin GitHub Actions to commit SHAs
- ✓ Review action permissions
- ✓ Treat build tools as privileged dependencies

**Containers:**
- ✓ Use specific version tags (never `latest`)
- ✓ Prefer official base images
- ✓ Pin image digests for reproducibility

**Production:**
- ✓ Treat dependency changes as significant events
- ✓ Test updates thoroughly before deployment
- ✓ Maintain rollback capability

## Example scenarios

**Scenario 1: Agent wants to add new Java library**

Agent behavior:
1. Checks library maintenance status
2. Verifies library is from Maven Central
3. Checks if library is > 6 months old
4. Reviews security advisories
5. Explains why library is needed and alternatives considered
6. **Waits for explicit approval** due to strict mode
7. Pins exact version in pom.xml
8. Creates focused PR with detailed rationale
9. Flags PR if library is from new publisher

**Scenario 2: Agent wants to update base container image**

Agent behavior:
1. Identifies new version (e.g., openjdk:17.0.8)
2. Checks for security advisories in new version
3. Explains why update is needed
4. Avoids `latest` tag - uses specific version
5. Considers pinning with SHA256 digest
6. Creates PR with:
   - Rationale for update
   - Security fixes addressed
   - Testing plan
   - Rollback procedure
7. Ensures update can be rolled back

**Scenario 3: Agent wants to add GitHub Action**

Agent behavior:
1. Verifies action publisher
2. Reviews action permissions required
3. Pins action to full commit SHA (not tag)
4. Explains what the action does
5. Highlights any elevated permissions
6. **Waits for approval** for privileged actions
7. Documents action purpose in workflow
8. Creates PR flagging new CI dependency

## What makes this "high autonomy" safe

Despite full autonomy, the agent is constrained by:

1. **Strict baseline**: Prevents risky dependency choices upfront
2. **Approval gates**: Requires confirmation for high-risk actions
3. **Visibility**: All changes are documented and reviewable
4. **Production context**: Extra stability and rollback considerations
5. **Artifact-specific rules**: CI actions and scanners get special treatment
6. **PR documentation**: Changes are explained and justified

The agent can work autonomously within these guardrails, but the guardrails ensure human oversight at critical decision points.

## Monitoring and adjustment

After deploying this configuration:

- Monitor agent suggestions that require approval
- Track frequency of risk signal triggers
- Adjust thresholds if too many false positives
- Review PR quality and documentation
- Update guardrails based on lessons learned

This configuration balances autonomy with safety for production systems.
