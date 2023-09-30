
# EKSctl Commands Cheat Sheet

This README provides a handy reference for common Amazon Elastic Kubernetes Service (EKS) CLI (eksctl) commands. EKSctl is a command-line tool provided by Weaveworks that simplifies the creation and management of EKS clusters. Make sure you have eksctl installed and configured before using these commands.

## Table of Contents

1. [Installation](#installation)
2. [Configuration](#configuration)
3. [Cluster Lifecycle](#cluster-lifecycle)
4. [Node Groups](#node-groups)
5. [Scaling](#scaling)
6. [EKS Operations](#eks-operations)
7. [SSH Access](#ssh-access)

## Installation

You can install eksctl by following the instructions in the [official eksctl documentation](https://eksctl.io/introduction/installation/).

## Configuration

Before using eksctl, configure your AWS credentials either by setting environment variables or using AWS CLI configuration:

```bash
aws configure
```

Ensure you have the necessary AWS IAM permissions to create and manage EKS clusters.

## Cluster Lifecycle

- Create an EKS cluster:
  ```bash
  eksctl create cluster --name my-cluster
  ```

- Delete an EKS cluster:
  ```bash
  eksctl delete cluster --name my-cluster
  ```

## Node Groups

- Create a node group:
  ```bash
  eksctl create nodegroup --cluster my-cluster --name my-nodegroup
  ```

- Delete a node group:
  ```bash
  eksctl delete nodegroup --cluster my-cluster --name my-nodegroup
  ```

## Scaling

- Scale a node group:
  ```bash
  eksctl scale nodegroup --cluster my-cluster --name my-nodegroup --nodes 4
  ```

- Autoscale a node group:
  ```bash
  eksctl scale nodegroup --cluster my-cluster --name my-nodegroup --nodes-min 2 --nodes-max 5
  ```

## EKS Operations

- Update an EKS cluster:
  ```bash
  eksctl update cluster --name my-cluster
  ```

- Get EKS cluster configuration:
  ```bash
  eksctl utils write-kubeconfig --cluster my-cluster
  ```

- List EKS clusters:
  ```bash
  eksctl get cluster
  ```

## SSH Access

- SSH into a node in the cluster (requires EC2 key pair):
  ```bash
  eksctl utils ssh --cluster my-cluster --region us-west-2 --name my-node
  ```


## Additional EKSctl Commands

### Upgrading EKS Cluster

- Upgrade an EKS cluster to a specific Kubernetes version:
  ```bash
  eksctl upgrade cluster --name my-cluster --kubernetes-version 1.21
  ```

### Managed Node Groups

- Create a managed node group:
  ```bash
  eksctl create nodegroup --cluster my-cluster --nodegroup-name my-managed-nodegroup --managed
  ```

- Delete a managed node group:
  ```bash
  eksctl delete nodegroup --cluster my-cluster --name my-managed-nodegroup
  ```

### Adding Add-Ons

- Add an AWS Fargate profile to the cluster:
  ```bash
  eksctl create fargateprofile --cluster my-cluster --name my-fargate-profile --namespace my-namespace
  ```

### EKS Managed Node Groups

- Create an EKS managed node group:
  ```bash
  eksctl create nodegroup --cluster my-cluster --managed --asg-access --name my-eks-managed-nodegroup
  ```

### Managing Node Labels

- Add labels to nodes in a node group:
  ```bash
  eksctl create nodegroup --cluster my-cluster --name my-nodegroup --node-labels key1=value1,key2=value2
  ```

- Update labels for nodes in a node group:
  ```bash
  eksctl update nodegroup --cluster my-cluster --name my-nodegroup --node-labels key3=value3
  ```

### Rolling Updates

- Perform a rolling update of a node group:
  ```bash
  eksctl update nodegroup --cluster my-cluster --name my-nodegroup --max-pods-per-node 15
  ```

### External DNS Integration

- Integrate with ExternalDNS for automatic DNS registration:
  ```bash
  eksctl utils associate-external-dns --cluster my-cluster --approve
  ```

### IAM OIDC Identity Provider

- Enable OIDC identity provider for your cluster:
  ```bash
  eksctl utils associate-iam-oidc-provider --region us-west-2 --cluster my-cluster
  ```

### Custom VPC Configuration

- Create an EKS cluster in a custom VPC:
  ```bash
  eksctl create cluster --name my-cluster --vpc-private-subnets=subnet-12345,subnet-67890
  ```

This README provides a quick reference to some common eksctl commands for managing Amazon EKS clusters. For more details and additional commands, refer to the [eksctl documentation](https://eksctl.io/usage/commands/).
 use case.
