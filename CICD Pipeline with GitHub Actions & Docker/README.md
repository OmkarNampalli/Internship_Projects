# CI/CD using Github Actions

## Project Overview

This project demonstrates a complete **CI/CD pipeline for a Node.js application**, showcasing how modern DevOps practices can be used to automate building, containerizing, and deploying applications to a Kubernetes cluster.

A demo **Node.js application** is used as the base application. The project integrates **GitHub Actions** to implement a Continuous Integration (CI) pipeline that automatically builds the application and creates a Docker image whenever changes are pushed to the repository. The built image is then pushed to **Docker Hub** for storage and distribution.

For deployment, a local Kubernetes environment is set up using **Minikube**. The application is deployed to the cluster using Kubernetes **Deployment** and **Service** manifests. The Deployment ensures the application runs reliably inside containers, while the Service exposes the application so it can be accessed externally.

This project highlights the workflow of:

* Automating builds with GitHub Actions
* Containerizing applications using Docker
* Publishing images to Docker Hub
* Deploying containerized applications to a Kubernetes cluster using Minikube
* Managing application lifecycle with Kubernetes Deployment and Service resources

Overall, the repository serves as a practical example of implementing a simple end-to-end DevOps pipeline for containerized applications.

---

## 🛠️ Tech Stack

* **Node.js** – Demo application
* **Docker** – Containerization
* **GitHub Actions** – CI/CD automation
* **Docker Hub** – Image registry
* **Kubernetes (Minikube)** – Container orchestration

---

## ⚙️ Workflow Overview

### 1. Code Push

Whenever code is pushed to the `main` branch:

* GitHub Actions workflow is triggered automatically.

### 2. Build & Push Docker Image

The workflow performs the following steps:

* Checks out the repository
* Builds a Docker image of the Node.js application
* Tags the image
* Pushes the image to Docker Hub

### 3. Deployment to Kubernetes

After the image is available in Docker Hub:

* Kubernetes manifests are applied to a local Minikube cluster
* The application is deployed using a Deployment resource
* The app is exposed using a Service resource

---

## 🔄 GitHub Actions Workflow

The CI/CD pipeline is defined in:

```
.github/workflows/main.yml
```

### Key Steps:

* Trigger: Push to `main` branch
* Build Docker image
* Login to Docker Hub
* Push image to repository

---

## 🐳 Docker Image

The Docker image:

* Uses Node.js base image
* Copies application code
* Installs dependencies
* Starts the application

### Build Locally (Optional)

```bash
docker build -t <your-dockerhub-username>/node-demo-app .
```

### Push Manually (Optional)

```bash
docker push <your-dockerhub-username>/node-demo-app
```

---

## ☸️ Kubernetes Deployment

### Start Minikube

```bash
minikube start
```

### Apply Manifests

```bash
kubectl apply -f deploy.yml
kubectl apply -f service.yml
```

### Verify Resources

```bash
kubectl get pods
kubectl get services
```

### Access Application

```bash
minikube service ‎github-actions-service
```

---

## 📦 Kubernetes Resources

### Deployment

* Manages application pods
* Pulls image from Docker Hub
* Ensures desired state

### Service

* Exposes the application
* Provides stable access endpoint

---

## 🔐 Secrets & Configuration

Make sure to configure the following secrets in your GitHub repository:

* `DOCKER_USERNAME`
* `DOCKER_PASSWORD`

---

## ✅ Key Features

* Automated CI/CD pipeline
* Dockerized application
* Seamless image push to Docker Hub
* Kubernetes deployment on Minikube
* End-to-end DevOps workflow

---

## 🚧 Future Improvements

* Add Helm charts for deployment
* Integrate monitoring (Prometheus + Grafana)
* Add ingress controller for external access
* Implement environment-based deployments

---

## 👨‍💻 Author

Omkar Nampalli
