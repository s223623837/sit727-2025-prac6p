# SIT737 - Cloud Native Application Development: Kubernetes Deployment

This repository contains a simple Node.js application with basic RESTful APIs, containerized with Docker, and deployed to a Kubernetes cluster. The project demonstrates the creation of a Kubernetes cluster, deployment of a containerized app, and interaction with it using Kubernetes commands.

## Project Overview
- **Application**: A Node.js app built with Express.js, providing CRUD APIs for managing a list of items.
- **Containerization**: Dockerized using a `Dockerfile`.
- **Kubernetes Resources**:
  - `pod.yaml`: Defines a single Pod for the app.
  - `app.yaml`: Combines a Deployment (2 replicas) and a Service (NodePort) for scalability and exposure.

## Prerequisites
- **Git**: For cloning and managing the repository.
- **Visual Studio Code**: For editing code (optional).
- **Node.js**: For running the app locally.
- **Docker**: For building and pushing the container image.
- **Minikube**: A local Kubernetes cluster (or another Kubernetes setup).
- **kubectl**: Kubernetes CLI for managing the cluster.

## Project Structure
my-node-app/
├── Dockerfile         # Docker configuration for the app
├── server.js          # Node.js application with APIs
├── package.json       # Node.js dependencies and scripts
├── package-lock.json  # Dependency lock file
├── app.yaml           # Combined Deployment and Service YAML
├── pod.yaml           # Single Pod YAML
└── README.md          # This documentation

## APIs
The app provides the following endpoints:
- `GET /api/items`: Retrieve all items.
- `GET /api/items/:id`: Retrieve a specific item by ID.
- `POST /api/items`: Add a new item (body: `{ "name": "Item Name" }`).
- `PUT /api/items/:id`: Update an item (body: `{ "name": "New Name" }`).
- `DELETE /api/items/:id`: Delete an item.

## Setup Instructions

### 1. Run Locally
1. Install dependencies:
   ```bash
   npm install
2. Start the app:
    ```bash
    npm start
3. Test the APIs (e.g., with curl)
    ```bash
    curl http://localhost:3000/api/items
    curl -X POST -H "Content-Type: application/json" -d '{"name":"Item 3"}' http://localhost:3000/api/items
### 2. Build and Push Docker Image
1. Build the Docker image:
   ```bash
   docker build -t bids4u/prace6p:latest .
2. Test locally (optional):
   ```bash
   docker run -p 3000:3000 yourusername/my-node-app:latest
3. Push to Docker Hub
   ```bash
    docker login
    docker push bids4u/prace6p:latest
### 3. Deploy to Kubernetes
1. Apply the combined YAML:
   ```bash
   kubectl apply -f app.yaml
2. Verify:
   ```bash
   kubectl get deployments
   kubectl get pods
   kubectl get services
