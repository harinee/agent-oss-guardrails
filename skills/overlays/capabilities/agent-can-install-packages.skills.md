# Agent Can Install Packages

Additional guidance when the agent has permission to install packages directly.

## When to use this

Apply this overlay when your agent can execute package manager commands (npm install, pip install, etc.).

## Instructions

### Before installing

- provide clear explanation of why the package is needed before installing
- explain what alternatives were considered
- highlight any risk signals (new package, unknown publisher, etc.)
- wait for confirmation if risk signals are present

### Installation behavior

- prefer modifying existing dependencies over adding new ones
- avoid installing packages speculatively or "just in case"
- avoid auto-installing dependencies without explanation
- ensure the package is recorded in manifest files (package.json, requirements.txt, etc.)

### Version specificity

- install specific versions, not latest or version ranges
- use exact version flags (npm install package@1.2.3, pip install package==1.2.3)
- avoid installing with flexible version specifiers

### Lockfile management

- ensure lockfiles are updated when packages are installed
- never delete lockfiles to resolve conflicts
- commit lockfile changes alongside manifest changes
- verify lockfile integrity after installation

### Hidden installs

- avoid installing global packages unless explicitly requested
- avoid installing system-level dependencies
- avoid installing packages outside the project directory
- ensure all installations are visible in project manifests

### Post-installation

- verify the package installed successfully
- document what was installed and why
- check for any unexpected dependencies that were added
- ensure the installation is reproducible
