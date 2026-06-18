# Core Concepts

## Cluster Setup
- Using Docker Desktop with kubeadm (single node)
- One node acts as both control-plane and worker

## Key Components (kube-system namespace)
- **kube-apiserver** - front door to the cluster, all kubectl commands go through here
- **etcd** - the cluster's database, stores all state
- **kube-scheduler** - decides which node a new Pod goes on
- **kube-controller-manager** - watches cluster state, ensures reality matches desired state
- **kube-proxy** - handles networking between Pods
- **coredns** - DNS for the cluster, lets Pods find each other by name

## Concepts
### Pod
- The smallest deployable unit in Kubernetes
- A wrapper around one or more containers
- Kubernetes never manages containers directly, always through Pods
- one Pod = one application instance
- Gets its own internal cluster IP on creation
- IPs are ephemeral — every new Pod gets a new IP
- Created imperatively: `kubectl run nginx --image=nginx`
- Created declaratively: `kubectl apply -f nginx-pod.yaml`


## Services
- Services allows a pod to accessed without sticking to the pod ip which is ephemeral
- the targetPort is the port that can be used to access an application in a pod


