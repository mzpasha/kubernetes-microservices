# Kubernetes Microservices Deployment with Jenkins

## 🔧 Tools Used
* Kubernetes: Container orchestration platform for deployment and scaling.

* Docker: To containerize individual microservices.

* kubectl: CLI to interact with the Kubernetes cluster.

* Minikube / Kind / EKS / AKS / GKE: For local or cloud Kubernetes cluster.

* Helm (optional): To manage applications via charts.

* GitHub Actions (optional): For CI/CD automation.

* Nginx Ingress Controller: To manage external access to services.

* Prometheus & Grafana (optional): For monitoring.



## 💡 Project Goal
To containerize and deploy multiple microservices (e.g., user service, product service) on a Kubernetes cluster using manifests and best practices like ConfigMaps, Secrets, and Ingress.

## 🔍 Features
Deploys 2–3 microservices (e.g., user-service, product-service, frontend)

Uses:

* Deployments and Services for each microservice

* ConfigMaps and Secrets for managing environment variables and credentials

* Persistent Volume (if needed) for storage

* Ingress controller for routing to services

* Scalable and self-healing (via Kubernetes ReplicaSets and health checks)

* Optionally monitored with Prometheus & Grafana

## 📦 Folder Structure
k8s-microservices-project/
│
├── services/
│   ├── user-service/
│   │   ├── Dockerfile
│   │   └── app.py / index.js / main.go
│   ├── product-service/
│   │   ├── Dockerfile
│   │   └── app.py / index.js / main.go
│   └── frontend/
│       ├── Dockerfile
│       └── index.html / app.js
│
├── k8s/
│   ├── user-service/
│   │   ├── deployment.yaml
│   │   └── service.yaml
│   ├── product-service/
│   │   ├── deployment.yaml
│   │   └── service.yaml
│   ├── frontend/
│   │   ├── deployment.yaml
│   │   └── service.yaml
│   ├── ingress.yaml
│   ├── configmap.yaml
│   └── secret.yaml
│
├── README.md
├── .gitignore


## 🚀 How to Run

🔧 Prerequisites
* Install Docker

* Install Kubernetes tool: Minikube (local), or use AKS/EKS/GKE

* Install kubectl

* (Optional) Install Helm for advanced setup

🛠️ Step-by-Step

1. Build Docker Images
   docker build -t user-service ./services/user-service
   docker build -t product-service ./services/product-service
   docker build -t frontend ./services/frontend

2. Push to Docker Hub (if using remote cluster)
   docker tag user-service <your_dockerhub>/user-service
   docker push <your_dockerhub>/user-service

3. Start Kubernetes Cluster
   minikube start

4. Apply Configurations
  kubectl apply -f k8s/configmap.yaml
  kubectl apply -f k8s/secret.yaml
  kubectl apply -f k8s/user-service/
  kubectl apply -f k8s/product-service/
  kubectl apply -f k8s/frontend/
  kubectl apply -f k8s/ingress.yaml

5. Enable Ingress (Minikube only)
   minikube addons enable ingress

6. Access the App
   minikube ip   # Or use localhost with ingress
 
## 🧠 Learning Outcome
* Understand Kubernetes core components: Pods, Services, Deployments, and Ingress.

* Learn to deploy and scale microservices in an orchestrated environment.

* Gain hands-on experience with kubectl and YAML manifests.

* Manage app configuration securely using ConfigMaps and Secrets.

* Handle internal and external service routing using ClusterIP, NodePort, and Ingress.

* Optionally integrate monitoring with Prometheus and Grafana.

* Optionally extend pipeline with CI/CD (GitHub Actions + Helm).
