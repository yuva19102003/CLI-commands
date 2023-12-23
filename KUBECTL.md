
# kubectl Commands Cheat Sheet

This README provides a handy reference for common `kubectl` commands. `kubectl` is the command-line tool for interacting with Kubernetes clusters. It allows you to manage and control Kubernetes resources.

`## Table of Contents

1. [Installation](#installation)
2. [Configuration](#configuration)
3. [Basic Commands](#basic-commands)
4. [Pod Management](#pod-management)
5. [Deployment Management](#deployment-management)
6. [Service Management](#service-management)
7. [Config Maps and Secrets](#config-maps-and-secrets)
8. [Node and Cluster Management](#node-and-cluster-management)
9. [Troubleshooting](#troubleshooting)
10. [Advanced Topics](#advanced-topics)`

## Installation

You can install `kubectl` by following the instructions in the [official Kubernetes documentation](https://kubernetes.io/docs/tasks/tools/install-kubectl/).

## Configuration

Before using `kubectl`, you need to configure it to point to your Kubernetes cluster. The configuration is typically stored in the `~/.kube/config` file. You can set the context for your cluster using:

```bash
kubectl config use-context my-cluster-context
```

## Basic Commands

- Get cluster information:
  ```bash
  kubectl cluster-info
  ```

- List all namespaces:
  ```bash
  kubectl get namespaces
  ```

- Switch to a different namespace:
  ```bash
  kubectl config set-context --current --namespace=my-namespace
  ```

- Get the status of all resources in the current namespace:
  ```bash
  kubectl get all
  ```

## Pod Management

- List pods in the current namespace:
  ```bash
  kubectl get pods
  ```

- Describe a pod:
  ```bash
  kubectl describe pod my-pod
  ```

- Create a pod from a YAML file:
  ```bash
  kubectl apply -f my-pod.yaml
  ```

- Delete a pod:
  ```bash
  kubectl delete pod my-pod
  ```

## Deployment Management

- List deployments in the current namespace:
  ```bash
  kubectl get deployments
  ```

- Scale a deployment:
  ```bash
  kubectl scale deployment my-deployment --replicas=3
  ```

- Rollout status of a deployment:
  ```bash
  kubectl rollout status deployment/my-deployment
  ```

## Service Management

- List services in the current namespace:
  ```bash
  kubectl get services
  ```

- Expose a deployment as a service:
  ```bash
  kubectl expose service <service name which going to change> --type=<ClusterIP NodeGroup LoaddBalancer> --target-port=<target port number> --name=<new service name>
  ```

## Config Maps and Secrets

- Create a ConfigMap from a file:
  ```bash
  kubectl create configmap my-config --from-file=config.properties
  ```

- Create a Secret from literal values:
  ```bash
  kubectl create secret generic my-secret --from-literal=username=admin --from-literal=password=secret
  ```

## Node and Cluster Management

- List nodes in the cluster:
  ```bash
  kubectl get nodes
  ```

- Drain a node for maintenance:
  ```bash
  kubectl drain my-node
  ```

- Uncordon a node after maintenance:
  ```bash
  kubectl uncordon my-node
  ```

## Troubleshooting

- View pod logs:
  ```bash
  kubectl logs my-pod
  ```

- Execute a command in a running pod:
  ```bash
  kubectl exec my-pod -- ls /app
  ```

## Advanced Topics

- Apply a manifest file:
  ```bash
  kubectl apply -f my-manifest.yaml
  ```

- Delete resources defined in a manifest file:
  ```bash
  kubectl delete -f my-manifest.yaml
  ```

- Get detailed information about cluster components:
  ```bash
  kubectl get componentstatuses
  ```

### Namespace Management

- Create a new namespace:
  ```bash
  kubectl create namespace my-namespace
  ```
- changing one namespace to another namespace:
  ```bash
    kubectl config set-context --current --namespace=my-namespace
  ```
  - view the current namespace:
  ```bash
  kubectl config view --minify --output 'jsonpath={..namespace}'
  ```
- Delete a namespace and all its resources:
  ```bash
  kubectl delete namespace my-namespace
  ```

### Labeling and Annotations

- Add labels to a resource (e.g., pod, service):
  ```bash
  kubectl label pod my-pod app=my-app
  ```

- List resources with specific labels:
  ```bash
  kubectl get pods -l app=my-app
  ```

### Resource Editing

- Edit a resource in your default text editor (e.g., Vim):
  ```bash
  kubectl edit deployment my-deployment
  ```

- Replace a resource using a YAML file:
  ```bash
  kubectl replace -f updated-pod.yaml
  ```

### Resource Deletion

- Delete all resources of a specific type in a namespace:
  ```bash
  kubectl delete pods,deployments,services --namespace my-namespace
  ```

- Delete all resources in the current namespace:
  ```bash
  kubectl delete all --all
  ```

### Resource Inspection

- Get detailed information about a specific resource type (e.g., nodes):
  ```bash
  kubectl describe nodes
  ```

### Port Forwarding

- Forward a local port to a pod's port for debugging:
  ```bash
  kubectl port-forward my-pod 8080:80
  ```

### Resource Validation

- Check if a YAML manifest is valid:
  ```bash
  kubectl apply --dry-run=client -f my-manifest.yaml
  ```

### Role-Based Access Control (RBAC)

- List roles and role bindings:
  ```bash
  kubectl get roles
  kubectl get rolebindings
  ```

- Describe a role or role binding:
  ```bash
  kubectl describe role my-role
  ```

### Custom Resource Definitions (CRDs)

- List Custom Resource Definitions:
  ```bash
  kubectl get crd
  ```

- Describe a Custom Resource:
  ```bash
  kubectl describe cr my-custom-resource
  ```


### Pod Forwarding

- Create a secure tunnel to a pod using the SSH protocol:
  ```bash
  kubectl port-forward --namespace my-namespace pod/my-pod 8888:8080
  ```

### Resource Metrics

- View resource usage metrics for pods:
  ```bash
  kubectl top pods
  ```

- View resource usage metrics for nodes:
  ```bash
  kubectl top nodes
  ```

### Pod Shell Access

- Open an interactive shell session in a running pod:
  ```bash
  kubectl exec -it my-pod -- /bin/bash
  ```

### Resource Quotas

- View resource quotas for a namespace:
  ```bash
  kubectl describe quota --namespace my-namespace
  ```

- Create a resource quota for a namespace:
  ```bash
  kubectl create quota my-resource-quota --hard=cpu=2,memory=4Gi,pods=10 --namespace my-namespace
  ```

### Rolling Updates and Rollbacks

- Perform a rolling update of a deployment with a new image:
  ```bash
  kubectl set image deployment/my-deployment my-container=my-image:latest
  ```

- Rollback a deployment to a previous revision:
  ```bash
  kubectl rollout undo deployment/my-deployment
  ```

### Pod Affinity and Anti-Affinity

- Define pod affinity based on node labels:
  ```bash
  kubectl describe pod my-pod --namespace my-namespace | grep "affinity:"
  ```

### Resource Validation with JSON Schema

- Validate a resource against a JSON schema:
  ```bash
  kubectl apply --dry-run=client -f my-manifest.yaml --validate=true
  ```

### Executing Commands on Multiple Pods

- Execute a command on multiple pods at once:
  ```bash
  kubectl exec -it $(kubectl get pods -o name) -- /bin/bash
  ```

### Namespace Resource Usage

- View resource usage across all namespaces:
  ```bash
  kubectl top pods --all-namespaces
  ```

### Pod Logs

- Stream live logs from a pod:
  ```bash
  kubectl logs -f my-pod
  ```

- Retrieve logs from a specific container in a multi-container pod:
  ```bash
  kubectl logs my-pod -c my-container
  ```

### Resource Port-Forwarding

- Forward a local port to a service's port:
  ```bash
  kubectl port-forward service/my-service 8888:80
  ```

### Custom Metrics

- View custom metrics for pods using tools like Prometheus:
  ```bash
  kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1" | jq .
  ```

### Resource Label Modification

- Add or modify labels to multiple pods using a selector:
  ```bash
  kubectl label pods -l app=my-app newlabel=my-label
  ```

### Resource Taints and Tolerations

- Taint a node to repel pods that do not tolerate the taint:
  ```bash
  kubectl taint nodes my-node key=value:taint-effect
  ```

- Tolerate a taint on a node by pods:
  ```bash
  kubectl annotate node my-node key=value:NoSchedule
  ```

### Resource Delete by Label

- Delete all pods with a specific label:
  ```bash
  kubectl delete pods -l app=my-app
  ```

### Rolling Restarts

- Perform a rolling restart of all pods in a deployment:
  ```bash
  kubectl rollout restart deployment/my-deployment
  ```

### Pod Priority and Preemption

- Set pod priority and preemption configuration:
  ```bash
  kubectl describe pod my-pod | grep "PriorityClass"
  ```

### Resource Events

- View events related to a resource:
  ```bash
  kubectl describe <resource-type> my-resource
  ```

### Resource Export

- Export a resource's configuration to a YAML file:
  ```bash
  kubectl get deployment my-deployment -o yaml > my-deployment-export.yaml
  ```

This README provides a quick reference to some common `kubectl` commands for managing Kubernetes clusters. For more details and additional commands, refer to the [kubectl documentation](https://kubernetes.io/docs/reference/kubectl/overview/).

