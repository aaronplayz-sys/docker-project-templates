# Python / FastAPI Example

This directory documents how to adapt the generic Python template for FastAPI.

Example `requirements.txt`:

```text
fastapi
uvicorn[standard]
```

Example runtime command:

```dockerfile
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

Pin dependencies using a lockfile or a fully pinned requirements file for reproducible deployments. Use a production-appropriate ASGI server configuration for your workload.
