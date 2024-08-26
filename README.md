 includes an overview, key concepts, commands, and a simple demo.

---

# Kubernetes Overview

Kubernetes (often abbreviated as K8s) is an open-source platform
designed to automate the deployment, scaling, and management of 
containerized applications. It provides a robust way to orchestrate
containerized applications across a cluster of machines.

## Importance of Kubernetes

- **Scalability**: Automatically scale applications up or down based on demand.
- **High Availability**: Distribute workloads to ensure high availability and fault tolerance.
- **Automation**: Automate deployment, updates, and rollback processes.
- **Consistency**: Ensure consistent environments across development, testing, and production.
- **Resource Management**: Efficiently manage resources and workloads across a cluster.

## Key Concepts

### 1. Pods

**Definition**: The smallest deployable units in Kubernetes that can contain one or more containers.

**Usage**:
- Group containers that need to share storage and network.
- Ensure containers in a pod run together on the same node.

### 2. Nodes

**Definition**: The physical or virtual machines in the Kubernetes cluster where containers are run.

**Components**:
- **Kubelet**: Manages the containers on a node.
- **Container Runtime**: Runs the containers.
- **Kube Proxy**: Handles networking and load balancing.

### 3. Services

**Definition**: An abstraction that defines a logical set of pods and a policy to access them.

**Types**:
- **ClusterIP**: Exposes the service on a cluster-internal IP.
- **NodePort**: Exposes the service on a static port on each node.
- **LoadBalancer**: Provisions an external load balancer to route traffic to the service.
- **ExternalName**: Maps the service to an external DNS name.

### 4. Deployments

**Definition**: Manages the deployment and scaling of pods. It ensures that the specified number of replicas of a pod are running.

**Features**:
- Rolling updates.
- Rollbacks to previous versions.

### 5. ConfigMaps and Secrets

**ConfigMaps**:
- Used to store non-sensitive configuration data.

**Secrets**:
- Used to store sensitive data like passwords, tokens, and keys.

### 6. Volumes

**Definition**: Provides storage for pods that persists beyond the lifecycle of individual containers.

**Types**:
- **EmptyDir**: Temporary storage that is cleared when the pod is removed.
- **HostPath**: Accesses files from the node’s filesystem.
- **PersistentVolumeClaim (PVC)**: Requests storage resources from the cluster.
- **CSI Volumes**: Interfaces with third-party storage solutions.

## Basic Commands

### Check Cluster Status

```bash
kubectl cluster-info
```

### Get Node List

```bash
kubectl get nodes
```

### Get Pod List

```bash
kubectl get pods
```

### Create a Deployment

```bash
kubectl create deployment my-deployment --image=nginx
```

### Expose a Deployment

```bash
kubectl expose deployment my-deployment --port=80 --target-port=80 --type=LoadBalancer
```

### Scale a Deployment

```bash
kubectl scale deployment my-deployment --replicas=3
```

### View Deployment Details

```bash
kubectl describe deployment my-deployment
```

### Apply Configuration from YAML File

```bash
kubectl apply -f deployment.yaml
```

### Delete a Deployment

```bash
kubectl delete deployment my-deployment
```

## Simple Demo

### 1. Create a Simple Deployment

```bash
kubectl create deployment demo --image=nginx
```

### 2. Expose the Deployment

```bash
kubectl expose deployment demo --port=80 --target-port=80 --type=NodePort
```

### 3. Check the Status of the Pod

```bash
kubectl get pods
```

### 4. Access the Application

To access the application, find the NodePort assigned by Kubernetes:

```bash
kubectl get services
```

Visit `http://<NodeIP>:<NodePort>` in your browser.

### 5. Scale the Deployment

```bash
kubectl scale deployment demo --replicas=3
```

### 6. Delete the Deployment and Service

```bash
kubectl delete deployment demo
kubectl delete service demo
```

## Conclusion

Kubernetes simplifies the deployment and management of containerized applications by providing powerful orchestration,
scaling, and automation features. By understanding its core concepts and commands, you can effectively manage and scale your applications in a Kubernetes environment.

---
## Architecture
<p align="center">
  <img src="https://phoenixnap.com/kb/wp-content/uploads/2021/04/full-kubernetes-model-architecture.png" width="750" title="architecture">
</p>
