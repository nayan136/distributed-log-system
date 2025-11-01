# Distributed Log Processing System

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Docker](https://img.shields.io/badge/Docker-Supported-blue.svg)](https://www.docker.com/)
[![Python](https://img.shields.io/badge/Python-3.8+-green.svg)](https://www.python.org/)

This project is part of the "365-Day Distributed Log Processing System Implementation" series - a comprehensive journey to build a production-ready distributed logging system from the ground up.

## 📋 Table of Contents

- [Project Overview](#-project-overview)
- [Features](#-features)
- [Getting Started](#-getting-started)
- [Project Structure](#-project-structure)
- [Configuration](#-configuration)
- [API Documentation](#-api-documentation)
- [Deployment](#-deployment)

## 🎯 Project Overview

We're building a distributed system for processing log data at scale. This system is designed to handle high-throughput logging scenarios with features like:

- **Distributed Architecture**: Multiple microservices working in harmony
- **Scalable Processing**: Handle millions of log entries per day
- **Real-time Analytics**: Process and analyze logs as they arrive
- **High Availability**: Fault-tolerant design with redundancy
- **Cloud-Native**: Containerized and orchestration-ready

## ✨ Features

### Current Features (Day 1)
- ✅ Basic logger service with multiple log levels
- ✅ Web interface for log monitoring
- ✅ Docker containerization
- ✅ Configurable log levels and frequency
- ✅ File and console logging
- ✅ RESTful API endpoints

## 🚀 Getting Started

### Prerequisites

Before you begin, ensure you have the following installed:

- **Docker** (v20.10+) and **Docker Compose** (v2.0+)
- **Git** (v2.30+)
- **Python** (v3.8+) - for local development
- **VS Code** (recommended) with Docker extension

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/nayan136/distributed-log-system.git
   cd distributed-log-processor
   ```

2. **Start the services**
   ```bash
   docker-compose up --build
   ```

3. **Access the application**
   - Web Interface: http://localhost:8000

4. **View logs**
   ```bash
   docker logs distributed-log-processor-logger-1 -f
   ```

### Manual Setup (Development)

For local development without Docker:

1. **Navigate to the logger service**
   ```bash
   cd src/services/logger
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the service**
   ```bash
   python app.py
   ```

## 📁 Project Structure

```
distributed-log-processor/
├── 📁 config/                 # Configuration files
├── 📁 data/                   # Data storage (gitignored)
├── 📁 docs/                   # Documentation
├── 📁 src/                    # Source code
│   └── 📁 services/           # Microservices
│       └── 📁 logger/         # Logger service
│           ├── app.py         # Main application
│           ├── logger.py      # Logger implementation
│           ├── web_server.py  # Create simple web server
│           ├── config.py      # Configuration management
│           ├── Dockerfile     # Container definition
│           └── requirements.txt # Python dependencies
├── 📁 tests/                  # Test suites
├── docker-compose.yml         # Container orchestration
├── .gitignore                # Git ignore rules
└── README.md                 # This file
```

## ⚙️ Configuration

The logger service can be configured using environment variables in the `docker-compose.yml` file:

| Environment Variable | Description | Default Value |
|----------------------|-------------|---------------|
| LOG_LEVEL | Minimum log level to output (DEBUG, INFO, WARNING, ERROR, CRITICAL) | INFO |
| LOG_FREQUENCY | How often to generate heartbeat logs (seconds) | 5.0 |
| LOG_TO_FILE | Whether to write logs to a file | true |
| LOG_FILE_PATH | Path where log files will be stored | /logs/logger.log |
| LOG_MAX_SIZE_MB | Maximum log file size before rotation (MB) | 1.0 |
| WEB_HOST | Host address for the web interface | 0.0.0.0 |
| WEB_PORT | Port for the web interface | 8080 |
| MAX_LOGS_TO_DISPLAY | Maximum number of logs to store in memory for the web interface | 100 |

## 📡 API Documentation

### Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/` | Web dashboard |
| `GET` | `/api/logs` | Retrieve recent logs |
| `GET` | `/api/config` | Get configs |

For detailed API documentation, see [docs/api.md](docs/api.md).


### Code Style

We follow PEP 8 guidelines for Python code. Use the following tools:

```bash
# Format code
black src/

# Lint code
flake8 src/

# Type checking
mypy src/
```

## 🚢 Deployment

### Docker Deployment

```bash
# Build and start services
docker-compose up --build -d

# View logs
docker-compose logs <container_name>
```