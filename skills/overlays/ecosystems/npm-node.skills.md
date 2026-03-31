# npm / Node.js Ecosystem

Specific guidance for Node.js projects using npm, yarn, or pnpm.

## When to use this

Apply this overlay to Node.js projects.

## Instructions

### Package selection

- prefer widely-used libraries with strong community adoption
- avoid adding heavy framework dependencies for simple tasks
- prefer native Node.js APIs when sufficient
- avoid packages that have been abandoned or deprecated
- check npm download counts and maintenance status

### Version management

- pin exact versions in package.json or use lockfiles
- commit package-lock.json, yarn.lock, or pnpm-lock.yaml
- avoid using `^` or `~` in version specifiers for production dependencies
- use exact versions for security-sensitive dependencies

### Dependencies vs devDependencies

- ensure packages are in the correct section (dependencies vs devDependencies)
- avoid installing dev dependencies in production builds
- keep devDependencies separate from runtime dependencies
- avoid unnecessary devDependencies

### Package.json maintenance

- respect existing package.json conventions
- avoid modifying scripts or configuration unnecessarily
- update package.json and lockfile together
- avoid introducing conflicting dependency versions

### Installation commands

- use `npm ci` for reproducible builds in CI/CD
- prefer `npm install package@1.2.3` with exact versions
- avoid `npm install` without version specifiers
- avoid `--force` flag unless explicitly needed and justified

### Security

- avoid packages with known vulnerabilities
- respect npm audit warnings
- avoid packages that make unexpected network requests
- be cautious of packages with install scripts (preinstall, postinstall)

### Node_modules

- never commit node_modules to version control
- rely on lockfiles for reproducibility
- avoid modifying files in node_modules directly
