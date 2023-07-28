# k8s_postgreSQL
Install and maintain PSQL stateful set on k8s local environment

# PostgreSQL Server in Kubernetes with kind

This repository provides a simple guide on how to deploy a PostgreSQL server in a Kubernetes cluster using `kind` (Kubernetes in Docker). It includes the necessary Kubernetes manifests and instructions to get you started quickly.

## Prerequisites

Before you begin, ensure you have the following tools installed:

- [Docker](https://www.docker.com/products/docker-desktop)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [kind](https://kind.sigs.k8s.io/docs/user/quick-start/)

## Getting Started

1. **Clone the Repository**

   ```bash
   git clone https://github.com/KrunalkumarRajdip/k8s_postgreSQL.git
   cd k8s_postgreSQL

Run the following commands to create a PostgreSQL server in your Kubernetes cluster:

### Step 1: Create Kubernetes Secret for PostgreSQL credentials
kubectl create secret generic postgres-credentials --from-literal=POSTGRES_USER=your_username --from-literal=POSTGRES_PASSWORD=your_password

### Step 2: Create Persistent Volume (PV) for PostgreSQL data
kubectl apply -f postgres-pv.yaml

### Step 3: Create Persistent Volume Claim (PVC) to bind to the PV
kubectl apply -f postgres-pvc.yaml

### Step 4: Deploy PostgreSQL using Kubernetes Deployment
kubectl apply -f postgres-deployment.yaml

### Step 5: Expose PostgreSQL using Kubernetes Service (LoadBalancer)
kubectl apply -f postgres-service.yaml


## Accessing PostgreSQL

After a few moments, the PostgreSQL server should be accessible using the LoadBalancer's external IP address or the appropriate service endpoint. You can connect to the server using your favorite PostgreSQL client.

## CleanUp:

- kubectl delete deployment postgres-deployment
- kubectl delete service postgres-service
- kubectl delete pvc postgres-pvc
- kubectl delete pv postgres-pv
- kubectl delete secret postgres-credentials
