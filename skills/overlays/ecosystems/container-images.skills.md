# Container Images

Specific guidance for selecting and using container images.

## When to use this

Apply this overlay when working with Docker images, Kubernetes manifests, or container-based deployments.

## Instructions

### Base image selection

- prefer official base images from Docker Hub or verified publishers
- avoid `latest` tag - use specific version tags
- prefer minimal base images (alpine, slim, distroless)
- avoid unnecessarily large base images
- verify image publishers before use

### Image tags

- use specific version tags (node:18.16.0, python:3.11.4)
- avoid mutable tags like `latest`, `stable`, or `main`
- avoid using branch names as tags
- pin image digests for maximum reproducibility (image@sha256:...)

### Image sources

- prefer Docker Hub official images
- prefer verified publisher images
- avoid images from unknown or unverified sources
- use organization-approved registries when available
- avoid pulling images from arbitrary registries

### Dockerfile practices

- minimize layers
- avoid downloading and executing scripts in Dockerfile
- avoid `curl | bash` patterns in RUN instructions
- use multi-stage builds to reduce final image size
- avoid storing secrets in images

### Image updates

- update base images intentionally, not automatically
- review base image changes before updating
- test image updates before deploying
- document why specific base images are used

### Security scanning

- scan images for vulnerabilities before use
- avoid images with critical vulnerabilities
- prefer images with minimal packages
- avoid images with unnecessary tools (shells, compilers) in production

### Image provenance

- prefer images with clear provenance information
- verify image signatures when available
- use content trust where supported
- avoid images with unclear build processes
