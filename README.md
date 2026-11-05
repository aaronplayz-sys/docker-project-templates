# Docker Project Templates

A personal collection of reusable Dockerfiles, Compose examples, and container engineering practices.

The goal is to build images that are secure, maintainable, reproducible, and appropriate for their workload—not merely shorter.

## Repository layout

- `templates/` — adaptable starting points for new projects.
- `examples/` — framework-specific reference implementations.
- `compose/` — reusable Compose patterns.
- `docs/` — engineering standards, security guidance, troubleshooting, and release checklists.

## Getting started

1. Choose the closest template under `templates/`.
2. Copy it into your project and adapt the runtime command, dependencies, ports, and writable paths.
3. Add or review the project's `.dockerignore`.
4. Build and run the image.
5. Verify that the process runs as a non-root user and required writes work.
6. Review [the production checklist](docs/production-checklist.md) before deployment.

## Core conventions

- Prefer official, maintained base images and pin a deliberate version.
- Run application processes as a dedicated non-root user.
- Install dependencies before copying frequently changing application source.
- Keep build-time dependencies out of runtime images where practical.
- Exclude secrets, local environments, caches, and repository metadata from the build context.
- Never bake secrets into image layers.
- Make writable paths explicit.
- Use health checks only when they accurately test application health.
- Prefer readable, auditable instructions over clever one-liners.

## Important

These are starting points, not universal production recipes. Adapt them to the application's framework, dependency manager, runtime, and deployment environment. Review base-image versions and framework recommendations when starting a new project.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).
