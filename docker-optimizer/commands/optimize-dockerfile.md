---
name: optimize-dockerfile
description: Analyze and optimize an existing Dockerfile
---

Analyze the user's existing Dockerfile and suggest optimizations.

**Process:**

1. Ask user to provide their current Dockerfile
2. Analyze for common issues:
   - Missing layer caching optimization
   - Running as root user
   - Large base images
   - Missing environment variables
   - No health checks
   - Inefficient COPY commands
   - Missing .dockerignore
   - Security vulnerabilities

3. Provide:
   - **Issues found** (with severity: high, medium, low)
   - **Optimized version** with changes highlighted
   - **Size estimation** (before/after if possible)
   - **Security improvements**
   - **Build time improvements**

**Analysis Categories:**

- ⚠️ **Security**: Root user, exposed secrets, outdated images
- 🚀 **Performance**: Layer caching, multi-stage builds, image size
- 📦 **Best Practices**: Python environment vars, system package cleanup
- 🔒 **Production Readiness**: Health checks, restart policies, logging

**Example Output:**
```
## Analysis Results

### Issues Found:

🔴 **HIGH** - Running as root user (Security risk)
🟡 **MEDIUM** - Using `python:3.11` instead of `python:3.11-slim` (344MB larger)
🟡 **MEDIUM** - Copying code before installing dependencies (Cache miss on every code change)
🟢 **LOW** - Missing Python environment variables

### Optimized Dockerfile:

[Provide improved version with inline comments explaining changes]

### Improvements:
- 🎯 Image size: 944MB → 198MB (79% reduction)
- ⚡ Build time: ~3min → ~30s (with cache)
- 🔒 Security: Root user removed, non-root user added
- 📈 Cache efficiency: Dependencies cached separately
```
