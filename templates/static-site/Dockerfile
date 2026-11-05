# Example static-site runtime image.
# Build the site in CI or a separate build stage, then copy its output here.
# nginx-unprivileged serves on 8080 without requiring root at runtime.
FROM nginxinc/nginx-unprivileged:1.28-alpine

# Replace dist/ with the actual output directory from your site generator.
COPY --chown=nginx:nginx dist/ /usr/share/nginx/html/

EXPOSE 8080
