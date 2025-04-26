# Langflow Deployment

This repository contains a Docker Compose configuration for deploying [Langflow](https://github.com/langflow-ai/langflow), an open-source UI for [LangChain](https://github.com/langchain-ai/langchain).

## Overview

Langflow is a UI for LangChain designed to provide a low-code way to experiment and prototype AI agents and workflows. This deployment includes:

- **Langflow**: Provides a visual interface for building and testing LangChain applications with drag-and-drop components
- **PostgreSQL**: Used as the primary database for storing Langflow's application data, including flows, components, and user information
- **Redis**: Handles chat memory and session management
- **Qdrant**: Provides vector storage capabilities for embeddings and semantic search features

## Prerequisites

- Docker
- Docker Compose

## Quick Start

1. Clone this repository:
   ```bash
   git clone git@github.com:jmcconne/langflow-deployment.git
   cd langflow-deployment
   ```

2. Start the services:
   ```bash
   docker compose up -d
   ```

3. Access Langflow:
   - Open your browser and navigate to `http://localhost:7860`

## Configuration

Connection details and settings for services:

- **Langflow**:
  - Host: `localhost`
  - Port: `7860`
  - Web UI: `http://localhost:7860`

- **PostgreSQL**:
  - Host: `postgres`
  - Database: `langflow`
  - Port: `5432`

- **Redis**:
  - Host: `redis`
  - Database: `0`
  - Port: `6379`

- **Qdrant**:
  - Host: `qdrant`
  - Ports: `6333` (HTTP), `6334` (gRPC)
  - Web UI: `http://localhost:6333/dashboard`

## Volumes

The following persistent volumes are created:
- `langflow-postgres`: PostgreSQL data
- `langflow-redis`: Redis data
- `langflow-qdrant`: Qdrant vector storage

## Health Checks

Most services include health checks to ensure proper startup and operation:
- Langflow: Checks port 7860 availability
- PostgreSQL: Verifies database readiness
- Redis: Tests connection with PING command

## Stopping the Services

To stop all services:
```bash
docker compose down
```

To stop and remove volumes (this will delete all data):
```bash
docker compose down -v
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details. 