# Kubernetes StatefulSets

A StatefulSet is used for applications that need a stable identity and persistent storage, such as databases.

Unlike a Deployment, where Pods are interchangeable, each Pod in a StatefulSet has its own name (for example `db-0`, `db-1`, `db-2`) and keeps that identity even after being recreated.

Each Pod also gets its own storage through `volumeClaimTemplates`. Kubernetes automatically creates a separate PersistentVolumeClaim (PVC) for every Pod, so they do not share the same disk.

This means that if a Pod crashes, Kubernetes recreates it with:
- the same name
- the same storage
- the same data

StatefulSets are therefore better choice for databases than Deployments. Databases need to keep their data and identity, while web servers and APIs usually do not.

## Deployment vs StatefulSet

Deployment:
- Best for stateless applications
- Pods are interchangeable
- Pod names change when recreated

StatefulSet:
- Best for stateful applications like databases
- Pods have stable names
- Each Pod has its own persistent storage
- Pods are created and deleted in order