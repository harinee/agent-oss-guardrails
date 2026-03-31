# Python / pip Ecosystem

Specific guidance for Python projects using pip, poetry, or conda.

## When to use this

Apply this overlay to Python projects.

## Instructions

### Package selection

- prefer maintained libraries with active PyPI presence
- avoid packages with setup.py scripts that download additional code
- prefer pure Python packages when possible
- check PyPI download statistics and maintenance status
- avoid packages that are wrappers around unmaintained C libraries

### Version management

- pin exact versions in requirements.txt (package==1.2.3)
- use requirements.txt or poetry.lock for reproducibility
- avoid version ranges in production requirements
- commit lockfiles (requirements.txt, poetry.lock, Pipfile.lock)

### Requirements files

- maintain separate requirements files if needed (requirements.txt, requirements-dev.txt)
- ensure all dependencies are recorded in requirements files
- avoid installing packages without adding them to requirements
- update requirements files when dependencies change

### Virtual environments

- use virtual environments (venv, virtualenv, poetry env)
- avoid installing packages globally
- avoid modifying system Python installation
- document virtual environment setup in project

### Installation commands

- use `pip install -r requirements.txt` for reproducible installs
- use `pip install package==1.2.3` with exact versions
- avoid `pip install --upgrade` without careful review
- avoid installing from git URLs unless necessary

### Security

- avoid packages with known vulnerabilities
- be cautious of packages with native extensions from unknown publishers
- avoid packages that execute code during installation
- respect pip audit or safety check warnings

### Build and distribution

- avoid packages that require complex build dependencies unnecessarily
- prefer wheels over source distributions for faster, safer installs
- avoid packages with unclear build processes
