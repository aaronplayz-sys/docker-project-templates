# Production Readiness Checklist

## Image

- [ ] Base image is trusted, maintained, and deliberately versioned.
- [ ] Dependencies are locked or otherwise reproducible.
- [ ] Build context excludes secrets, local environments, caches, and repository metadata.
- [ ] Build-only dependencies are excluded from the runtime stage where practical.
- [ ] Image has been scanned for known vulnerabilities.

## Runtime

- [ ] Application runs as non-root.
- [ ] Runtime command uses exec form.
- [ ] Application binds to the correct interface.
- [ ] Writable paths are explicit and tested.
- [ ] Logs go to stdout/stderr.
- [ ] Graceful shutdown is supported.
- [ ] Health check reflects actual application health, if configured.

## Deployment

- [ ] Secrets are injected securely at runtime.
- [ ] Persistent data has an explicit storage strategy.
- [ ] Ports and networks are intentionally exposed.
- [ ] Resource limits and restart behavior are considered.
- [ ] Backup, restore, and update procedures are documented.
