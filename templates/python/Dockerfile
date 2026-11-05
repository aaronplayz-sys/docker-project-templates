# Generic Python application template.
# Adapt the Python version, OS packages, dependency manager, and command.
FROM python:3.13-slim-bookworm

ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

RUN apt-get update \
    && apt-get install -y --no-install-recommends ca-certificates \
    && rm -rf /var/lib/apt/lists/*

RUN groupadd --system app \
    && useradd --system --gid app --create-home --home-dir /app app

WORKDIR /app

# This example assumes requirements.txt. Adapt for uv, Poetry, or another tool.
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

COPY --chown=app:app . .

# Create only paths that the application needs to write.
RUN mkdir -p /app/data /app/logs \
    && chown app:app /app/data /app/logs

USER app

# Replace with the correct port and application command.
EXPOSE 8000
CMD ["python", "main.py"]
