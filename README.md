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
   - **Frontend:**
   ```bash
   docker build -t frontend-image ./frontend
   ```
   - **Backend:**
   ```bash
   docker build -t backend-image ./backend
   ```
3. **Run the Application:**
   ```bash
   docker-compose up
   ```
4. **Access the Application:**
   ```bash
   Frontend: http://localhost:3000
   Backend: http://localhost:5000
#Cluster Deployment Using Kubernetes
##Objective
Deploy the application to a Kubernetes cluster for a production-like environment.

##Architecture
Deployments: Each service is managed via Kubernetes Deployment objects.
Services:
MongoDB and backend use ClusterIP for internal communication.
Frontend uses a NodePort service for external access.
Networking: Managed using Kubernetes internal DNS.
Steps to Deploy
Start Minikube:

   
