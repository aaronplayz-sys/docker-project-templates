# Container Security

- Run as non-root unless a documented requirement prevents it.
- Do not place secrets in `ARG`, `ENV`, image layers, or build logs.
- Use BuildKit secret mounts for credentials needed during builds.
- Minimize installed packages and remove package-manager metadata.
- Keep base images and dependencies updated.
- Scan images and dependencies in CI.
- Consider a read-only root filesystem; provide explicit writable mounts or paths where needed.
- Drop Linux capabilities the application does not need.
- Consider `no-new-privileges` and resource limits at deployment time.
- Do not expose ports or publish services unless required.
- Treat third-party images and build-context files as supply-chain inputs.

Security controls must be tested against the actual workload. Do not copy hardening flags blindly.
