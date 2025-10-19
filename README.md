# Docker Optimizer Plugin for Claude Code

Production-ready Docker tooling with specialized AI agents for Python applications.

## 🚀 Features

- **dockerfile-expert**: Creates optimized, secure Dockerfiles with multi-stage builds
- **compose-architect**: Designs complete Docker Compose setups with multiple services
- **4 Slash Commands**: Quick access to common Docker workflows
- **Production-Ready**: Security, optimization, and best practices built-in

## 📦 Installation
```bash
# Add marketplace
claude /plugin marketplace add yourusername/docker-optimizer-marketplace

# Install plugin
claude /plugin install docker-optimizer@docker-optimizer-marketplace

# Verify
claude /help
```

## 🎯 Usage

### Generate Dockerfile
```bash
claude /agent dockerfile-expert

> "I need a Dockerfile for my FastAPI application"
```

The agent will ask questions and generate an optimized Dockerfile with:
- Multi-stage build
- Non-root user
- Health checks
- Proper caching
- Security best practices

### Generate Docker Compose
```bash
claude /agent compose-architect

> "I need Docker Compose with PostgreSQL, Redis, and Celery workers"
```

The agent will generate a complete setup with:
- All services configured
- Health checks and dependencies
- Named volumes
- .env file template
- Production-ready configuration

### Quick Commands
```bash
# Generate Dockerfile
claude /generate-dockerfile

# Generate Docker Compose
claude /generate-compose

# Optimize existing Dockerfile
claude /optimize-dockerfile

# Complete setup (Dockerfile + Compose)
claude /full-stack-setup
```

## 📋 What You Get

### From dockerfile-expert:
- Optimized Dockerfile with multi-stage build
- .dockerignore file
- Build and run commands
- Framework-specific configurations (Flask, FastAPI, Django, etc.)
- Image size optimization
- Security hardening

### From compose-architect:
- Complete docker-compose.yml
- Service orchestration
- Health checks for all services
- Named volumes for persistence
- .env file template
- Development and production configurations
- Common commands cheat sheet

## 🏗️ Example Workflow
```bash
# Start Claude
claude

# Get Dockerfile
/agent dockerfile-expert
> "Create Dockerfile for my Flask app with requirements.txt on port 5000"

# Get Docker Compose
/agent compose-architect  
> "Add PostgreSQL and Redis to my Flask setup"

# You now have:
# - Dockerfile (optimized, secure)
# - docker-compose.yml (complete stack)
# - .dockerignore
# - .env template

# Build and run
docker-compose up --build
```

## 🔥 Agents

### dockerfile-expert
Specializes in:
- Multi-stage builds
- Layer caching optimization
- Security (non-root users, minimal images)
- Python-specific best practices
- Framework configurations (Flask, FastAPI, Django, Streamlit)

### compose-architect
Specializes in:
- Multi-service orchestration
- Database integration (PostgreSQL, MySQL, MongoDB)
- Caching (Redis, Memcached)
- Message queues (RabbitMQ, Celery)
- Production deployments

## 📚 Best Practices Included

- ✅ Multi-stage builds for minimal image size
- ✅ Non-root users for security
- ✅ Health checks for all services
- ✅ Proper layer caching
- ✅ Environment variable management
- ✅ Named volumes for data persistence
- ✅ Service dependencies and health checks
- ✅ Resource limits for production
- ✅ Logging configuration

## 🛠️ Supported Frameworks

- Flask (with Gunicorn)
- FastAPI (with Uvicorn)
- Django (with Gunicorn)
- Streamlit
- CLI tools
- Data science apps

## 🤝 Contributing

Issues and PRs welcome at https://github.com/yourusername/docker-optimizer-marketplace

## 📄 License

MIT
