# Sandy5688-Ignite-lab-Dev-C-Ai-agent
# AI Agent - Production-Ready Adaptive Interaction Service

[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://python.org)
[![Docker](https://img.shields.io/badge/docker-ready-blue.svg)](Dockerfile)
[![Tests](https://img.shields.io/badge/tests-passing-green.svg)](tests/)

A production-ready AI-powered conversation management system with multi-assistant routing, negotiation logic, human override capabilities, and enterprise-grade security.

## 🚀 Quick Start

### Docker Deployment (Recommended)

```bash
# Clone the repository
git clone <repo-url>
cd ai-agent

# Copy environment template
cp .env.example .env

# Deploy with one command
powershell -ExecutionPolicy Bypass -File scripts/deploy.ps1 -Environment production -Build -Migrate -Test
```

### Manual Installation

```bash
# Install dependencies
pip install -r requirements.txt

# Set up environment
cp .env.example .env

# Run the service
python app.py
```

## 🧪 Smoke Test

```bash
# Start stack (Docker)
docker-compose up -d --build

# Health check should return 200
curl http://localhost:5000/health
```

## 📁 Project Structure

```
ai-agent/
├── ai_agent/                 # Main package
│   ├── core/                # Business logic
│   │   ├── orchestrator.py  # Dialogue management
│   │   ├── escalation.py    # Escalation handling
│   │   └── assistants.py    # Assistant routing
│   ├── database/            # Data layer
│   │   ├── models.py        # Database models
│   │   └── operations.py    # Database operations
│   ├── auth/                # Authentication
│   │   └── jwt_manager.py   # JWT handling
│   ├── api/                 # API layer
│   │   ├── endpoints.py     # Flask routes
│   │   └── schemas.py       # Request/response schemas
│   └── utils/               # Utilities
│       ├── metrics.py       # Prometheus metrics
│       ├── rate_limiter.py  # Rate limiting
│       └── logging_config.py # Structured logging
├── config/                  # Configuration files
│   ├── config.env.development
│   ├── config.env.production
│   ├── alembic.ini
│   └── migrations/          # Database migrations
├── tests/                   # Test suite
│   ├── test_app.py
│   └── pytest.ini
├── docs/                    # Documentation
│   ├── README.md
│   ├── PRODUCTION_READY_SUMMARY.md
│   └── DOCKER_DEPLOYMENT.md
├── scripts/                 # Deployment scripts
│   ├── deploy.ps1
│   ├── test-docker.ps1
│   └── test-docker.sh
├── logs/                    # Application logs
├── app.py                   # Main application entry point
├── setup.py                 # Package installation
├── requirements.txt         # Python dependencies
├── Dockerfile              # Container configuration
├── docker-compose.yml      # Multi-service deployment
└── .dockerignore           # Docker build optimization
```

## 🎯 Key Features

### ✅ Production-Ready
- **PostgreSQL Database** with proper indexing
- **JWT Authentication** with Bearer tokens
- **Rate Limiting** to prevent abuse
- **Structured Logging** with rotation
- **Prometheus Metrics** for monitoring
- **Docker Deployment** with health checks

### ✅ Conversation Integrity
- **Human Override Mode** prevents AI double-responding
- **Conversation State Management** tracks AI vs human control
- **Escalation Integration** with automatic mode switching
- **Explicit Resume Logic** for AI resumption

### ✅ Multi-Assistant Support
- **Negotiation Assistant** (fully implemented)
- **Content Assistant** (placeholder)
- **Outreach Assistant** (placeholder)
- **Metrics Assistant** (placeholder)

### ✅ Enterprise Security
- **Request Validation** with Pydantic schemas
- **CORS Configuration** for cross-origin security
- **Error Handling** with standardized responses
- **Health Monitoring** with database connectivity

## 📡 API Endpoints

### Authentication
```bash
# Get token
curl -X POST http://localhost:5000/auth/token
```

### Core Endpoints
```bash
# Main interaction
curl -X POST http://localhost:5000/interact \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{"record_id": "123", "inquiry_text": "What is the price?"}'

# Escalation
curl -X POST http://localhost:5000/handover \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{"record_id": "123", "reason": "commitment_detected"}'

# Conversation mode
curl -X POST http://localhost:5000/conversation/mode \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{"record_id": "123", "mode": "human_override"}'
```

### Monitoring
```bash
# Health check
curl http://localhost:5000/health

# Metrics
curl http://localhost:5000/metrics
```

## 🔧 Configuration

- Use `.env.example` as a template; copy to `.env` and fill values.
- Key variables: `DATABASE_URL`, `JWT_SECRET_KEY`, `CORS_ORIGINS`, `ACTIVE_ASSISTANTS`, `LOG_LEVEL`.

## 🧪 Testing

```bash
# Run tests
pytest

# Run with coverage
pytest --cov=ai_agent --cov-report=term-missing
```

## 🐳 Deployment

```bash
# Quick deployment
docker-compose up -d

# With custom configuration
cp .env.example .env
# edit .env as needed
docker-compose up -d --build
```

## 📊 Monitoring

- **Health Checks**: `/health` endpoint
- **Prometheus Metrics**: `/metrics` endpoint
- **Structured Logs**: JSON format with rotation
- **Database Monitoring**: Connection status tracking

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests
5. Submit a pull request

## 📞 Support

For issues and questions, please refer to the documentation or contact the development team.

---

**Ready for production deployment with confidence!** 🎉
