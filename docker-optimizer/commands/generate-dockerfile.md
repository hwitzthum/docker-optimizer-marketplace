---
name: generate-dockerfile
description: Generate an optimized Dockerfile for a Python application
---

Generate a production-ready, optimized Dockerfile for a Python application.

**Ask the user these questions first:**

1. **Python version** (e.g., 3.11, 3.12)
2. **Application type** (Flask, FastAPI, Django, CLI tool, data science)
3. **Dependencies management** (requirements.txt, poetry, pipenv, uv)
4. **Port** (if web application)
5. **Additional system dependencies** (e.g., PostgreSQL client, image processing libraries)

**Then generate a Dockerfile with these optimizations:**

## Best Practices to Follow

1. **Use specific Python version with slim variant** (e.g., `python:3.11-slim`)
2. **Multi-stage builds** for smaller images (if needed)
3. **Layer caching optimization** - Copy requirements before code
4. **Non-root user** for security
5. **Environment variables** for Python optimization:
   - `PYTHONUNBUFFERED=1` (immediate output)
   - `PYTHONDONTWRITEBYTECODE=1` (no .pyc files)
   - `PIP_NO_CACHE_DIR=1` (smaller image)
6. **Health checks** (for web apps)
7. **.dockerignore recommendations**

## Example Output Structure
```dockerfile
# Use specific version
FROM python:3.11-slim

# Set environment variables
ENV PYTHONUNBUFFERED=1 \
    PYTHONDONTWRITEBYTECODE=1 \
    PIP_NO_CACHE_DIR=1

# Install system dependencies (if needed)
RUN apt-get update && apt-get install -y --no-install-recommends \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Create non-root user
RUN useradd -m -u 1000 appuser

# Set working directory
WORKDIR /app

# Copy and install dependencies (as root for permissions)
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . .

# Change ownership
RUN chown -R appuser:appuser /app

# Switch to non-root user
USER appuser

# Expose port (if web app)
EXPOSE 8000

# Health check (if web app)
HEALTHCHECK --interval=30s --timeout=3s --start-period=40s \
  CMD python -c "import requests; requests.get('http://localhost:8000/health')"

# Run application
CMD ["python", "app.py"]
```

**Also provide:**
- Recommended `.dockerignore` file
- Build command
- Run command with common flags
- Security recommendations
