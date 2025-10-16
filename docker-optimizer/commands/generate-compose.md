---
name: generate-compose
description: Generate a Docker Compose file for multi-service Python applications
---

Generate a production-ready Docker Compose configuration.

**Ask the user:**

1. **Services needed** (e.g., web app, database, redis, celery workers)
2. **Database type** (PostgreSQL, MySQL, MongoDB, none)
3. **Caching** (Redis, Memcached, none)
4. **Message queue** (RabbitMQ, Redis, none)
5. **Development or Production** setup

**Generate with these features:**

## Best Practices

1. **Service networking** - proper depends_on and health checks
2. **Environment variables** - use .env file
3. **Volumes** for data persistence
4. **Named volumes** for databases
5. **Bind mounts** for development (code sync)
6. **Resource limits** for production
7. **Health checks** for all services
8. **Restart policies**

## Example Structure
```yaml
version: '3.8'

services:
  web:
    build: .
    ports:
      - "8000:8000"
    environment:
      - DATABASE_URL=postgresql://user:password@db:5432/appdb
      - REDIS_URL=redis://redis:6379/0
    depends_on:
      db:
        condition: service_healthy
      redis:
        condition: service_healthy
    volumes:
      - .:/app  # Development only
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:8000/health"]
      interval: 30s
      timeout: 3s
      retries: 3
    
  db:
    image: postgres:15-alpine
    environment:
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=password
      - POSTGRES_DB=appdb
    volumes:
      - postgres_data:/var/lib/postgresql/data
    restart: unless-stopped
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U user"]
      interval: 10s
      timeout: 5s
      retries: 5
    
  redis:
    image: redis:7-alpine
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]
      interval: 10s
      timeout: 3s
      retries: 3
    volumes:
      - redis_data:/data

volumes:
  postgres_data:
  redis_data:
```

**Also provide:**
- Sample .env file
- Commands to run (up, down, logs, etc.)
- Development vs production differences
- Networking explanations
