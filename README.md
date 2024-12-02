# Multi-Container Application Deployment

This repository contains the deployment files and configurations for a multi-container application comprising a React frontend, Node.js backend, and MongoDB database. The application can be deployed locally using Docker Compose or on a Kubernetes cluster using Minikube.

## Project Overview

The application architecture consists of:
- **Frontend**: A React application serving as the user interface.
- **Backend**: A Node.js API server.
- **Database**: A MongoDB instance for data storage.

The deployment is designed for scalability, reliability, and ease of management.

---

## Local Deployment Using Docker Compose

### Objective
Run the application locally to test its functionality and container interactions.

### Architecture
- Services are orchestrated via a `docker-compose.yml` file.
- Containers communicate over a custom bridge network (`techdome-network`).
- MongoDB uses a volume (`mongo-data`) for persistent data storage.

### Steps to Deploy
1. **Clone the Repository**:
   ```bash
   git clone <repository-url>
   cd <repository-name>

2. **Build Application Images**:
   Frontend:
   ```bash
   docker build -t frontend-image ./frontend
   ```
   Backend:
   ```bash
   docker build -t backend-image ./backend
```
