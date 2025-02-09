# MongoDB Kubernetes Deployment

This repository contains Kubernetes configuration files for deploying MongoDB and Mongo Express using ConfigMap and Secret management.

## Overview

The setup includes:
- **MongoDB**: A NoSQL database deployed with a Kubernetes `Deployment` and exposed via a `Service`.
- **Mongo Express**: A web-based MongoDB administrative interface.
- **ConfigMap & Secrets**: Used for managing sensitive credentials and database configuration.

## Components

### 1. ConfigMap
- Stores MongoDB host configuration.
- Defined in `mongodb-configmap`.

### 2. Secret
- Contains encoded MongoDB credentials.
- Defined in `mongodb-secret`.

### 3. MongoDB Deployment
- Deploys a single replica of MongoDB.
- Uses credentials from `mongodb-secret`.

### 4. MongoDB Service
- Exposes MongoDB internally within the Kubernetes cluster.

### 5. Mongo Express Deployment
- Provides a web-based UI for MongoDB administration.
- Connects to MongoDB using credentials from `mongodb-secret` and host from `mongodb-configmap`.

### 6. Mongo Express Service
- Exposes Mongo Express via a `LoadBalancer` service on port `30000`.

## Deployment Instructions

1. **Apply ConfigMap and Secret:**
   ```sh
   kubectl apply -f mongodb-config-components.yaml

