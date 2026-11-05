# Troubleshooting

## Permission denied

1. Identify the effective UID/GID with `id`.
2. Identify the exact path the application needs to write.
3. Check ownership and permissions inside the image and on mounted volumes.
4. Fix only the required path; avoid making the whole application tree world-writable.
5. Remember that bind-mount ownership comes from the host.

## Dependency changes are not appearing

- Confirm the dependency manifest and lockfile are copied before installation.
- Rebuild after changing dependency files.
- Use `docker build --no-cache` only to diagnose cache-related problems, not as the default workflow.

## Container exits immediately

- Inspect `docker logs`.
- Confirm `CMD` points to the correct executable or module.
- Check required environment variables and mounted files.
- Run the image interactively for diagnosis without unnecessarily changing the production command.

## Application is unreachable

- Bind the application to `0.0.0.0`, not only `127.0.0.1`.
- Confirm the container port and host port mapping.
- Check firewall, reverse-proxy, and network configuration.
