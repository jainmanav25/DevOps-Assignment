
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
   ```

2. **Build Application Images**:
   - **Frontend**:
     ```bash
     docker build -t frontend-image ./frontend
     ```
   - **Backend**:
     ```bash
     docker build -t backend-image ./backend
     ```

3. **Run the Application**:
   ```bash
   docker-compose up
   ```

4. **Access the Application**:
   - Frontend: [http://localhost:3000](http://localhost:3000)
   - Backend: [http://localhost:5000](http://localhost:5000)

---

## Cluster Deployment Using Kubernetes

### Objective
Deploy the application to a Kubernetes cluster for a production-like environment.

### Architecture
- **Deployments**: Each service is managed via Kubernetes Deployment objects.
- **Services**:
  - MongoDB and backend use `ClusterIP` for internal communication.
  - Frontend uses a `NodePort` service for external access.
- **Networking**: Managed using Kubernetes internal DNS.

### Steps to Deploy
1. **Start Minikube**:
   ```bash
   minikube start
   ```

2. **Deploy MongoDB**:
   ```bash
   kubectl apply -f k8s/mongo-deployment.yaml
   ```

3. **Deploy Backend**:
   ```bash
   kubectl apply -f k8s/backend-deployment.yaml
   ```

4. **Deploy Frontend**:
   ```bash
   kubectl apply -f k8s/frontend-deployment.yaml
   ```

5. **Access the Application**:
   ```bash
   minikube service frontend-service
   ```
   Open the displayed URL in a browser.

---

## Managing the Application

### Scaling
Increase the number of pods for high availability:
```bash
kubectl scale deployment frontend --replicas=3
```

### Autoscaling
Set up Horizontal Pod Autoscaler for the backend:
```bash
kubectl autoscale deployment backend --cpu-percent=50 --min=1 --max=10
```

### Monitoring
Check the status of all pods and services:
```bash
kubectl get pods
kubectl get services
```

### Rollbacks
Rollback to a previous version of a deployment:
```bash
kubectl rollout undo deployment backend
```

---

## Demonstration

### Local Testing
1. Start the application using Docker Compose:
   ```bash
   docker-compose up
   ```
2. Access the frontend and verify integration with the backend and database.

### Cluster Deployment
1. Deploy the application to Minikube:
   ```bash
   minikube start
   kubectl apply -f k8s/
   ```
2. Verify pod and service statuses:
   ```bash
   kubectl get pods
   kubectl get services
   ```
3. Access the frontend service via Minikube and demonstrate full functionality.

---

## Files in This Repository

- **Dockerfiles**:
  - `frontend/Dockerfile`
  - `backend/Dockerfile`
- **Docker Compose**:
  - `docker-compose.yml`
- **Kubernetes Manifests**:
  - `k8s/mongo-deployment.yaml`
  - `k8s/backend-deployment.yaml`
  - `k8s/frontend-deployment.yaml`

---

## Prerequisites

- **Docker** and **Docker Compose**
- **Minikube** and **kubectl**
- Node.js and npm for application development (if needed)

---

