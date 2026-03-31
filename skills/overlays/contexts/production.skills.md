# Production Context

Stricter guidance for production systems and customer-facing applications.

## When to use this

Apply this overlay to production systems, customer-facing applications, or business-critical services.

## Instructions

### Stability priority

- prefer stable, well-tested releases
- avoid experimental or alpha/beta packages
- prefer packages with established track records in production
- avoid frequent dependency churn

### Change management

- treat dependency changes as significant events requiring review
- test dependency updates thoroughly before production deployment
- document dependency update rationale
- prefer gradual rollout of dependency updates

### Maintenance and support

- prefer packages with active maintenance and security response
- prefer packages with clear support channels
- avoid packages that appear abandoned or unmaintained
- verify that packages have security disclosure processes

### Version management

- pin exact versions with no flexibility
- avoid version ranges
- document version selection rationale
- maintain dependency update changelog

### Risk assessment

Before adding production dependencies, assess:
- package stability and production readiness
- maintenance status and security response
- breaking change history
- community adoption in production environments

### Monitoring and observability

- monitor dependency health in production
- track dependency-related errors and issues
- maintain inventory of production dependencies
- plan for dependency incident response

### Rollback readiness

- ensure dependency changes can be rolled back
- test rollback procedures
- maintain previous known-good dependency versions
- document rollback process for dependency issues
