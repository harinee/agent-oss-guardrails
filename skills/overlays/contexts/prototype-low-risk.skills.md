# Prototype / Low Risk Context

Relaxed guidance for prototypes, experiments, and low-risk projects.

## When to use this

Apply this overlay to prototype projects, proof-of-concepts, personal experiments, or low-risk development.

## Instructions

### Experimentation allowed

- allow faster iteration and experimentation
- permit trying new or less-established packages for evaluation
- allow testing experimental features and frameworks
- permit more flexible dependency exploration

### Still maintain baselines

- still avoid unnecessary dependencies
- still prefer maintained packages when practical
- still pin versions for reproducibility
- still record dependencies in manifests

### Version management

- pin versions for reproducibility, even in prototypes
- commit lockfiles to allow others to reproduce the prototype
- document significant dependency choices for potential production migration

### Risk awareness

- acknowledge that prototype dependencies may not be production-ready
- document any dependencies that would need review before production
- avoid developing production patterns that rely on untested packages
- plan for dependency re-evaluation if prototype becomes production code

### Migration considerations

If the prototype may become production code:
- document dependency choices and rationale
- flag any dependencies that need production review
- prefer dependencies that could scale to production
- avoid accumulating technical debt that blocks production use

### Learning and evaluation

- use prototypes to evaluate new packages and tools safely
- document lessons learned about dependency choices
- share findings about package quality and maintenance
- treat prototypes as opportunities to test guardrails safely
