# Docker Engineering Standards

## Images and reproducibility

- Prefer official images from trusted publishers.
- Select an explicit image version; avoid `latest` for repeatable deployments.
- For stricter supply-chain controls, consider pinning image digests and defining an update process.
- Rebuild regularly to receive base-image security updates.

## Build layers and caching

- Copy dependency manifests and lockfiles before application source.
- Install dependencies in a separate layer where this improves cache reuse.
- Combine related package-manager operations and clean package indexes in the same layer.
- Do not combine unrelated operations merely to reduce line count.

## Users and permissions

- Create a dedicated unprivileged runtime user.
- Use `COPY --chown` where it is appropriate.
- Create only directories the application must write to.
- Avoid broad recursive ownership changes when a narrower path is sufficient.
- Switch to `USER` before the runtime command.

## Runtime

- Use exec-form `CMD` and `ENTRYPOINT` so the application receives signals correctly.
- Keep containers focused on one primary service.
- Write logs to stdout/stderr.
- Configure graceful shutdown and sensible timeouts in the application server.
- Do not assume a container filesystem is persistent.

## Configuration and secrets

- Supply non-secret configuration through environment variables or mounted configuration.
- Supply secrets through the deployment platform's secret mechanism.
- Never copy `.env` files, private keys, tokens, or credentials into an image.
- Document required variables and safe defaults.

## Multi-stage builds

Use multi-stage builds when compilation, asset generation, or dependency installation needs tools that are unnecessary at runtime. Keep the final stage focused on runtime requirements.

## Health checks

Add a Docker `HEALTHCHECK` only when a reliable local health command or endpoint exists. Distinguish liveness from readiness; Compose dependency ordering alone does not guarantee that a dependency is ready.
