---
description: Container orchestration tool
---

# Kubernetes

## What it is?

### Definition

* Container orchestration Tool by Google
* Help manage containerized applications in different environment

### Problem Solved

* Increase microservices leads to increased usage of containers
* Demand for proper way to manage hundreds of containers
* High availability
* Scalability
* Disaster recovery

### Architecture

* At least 1 **Master Node** (Run important processes, API Server+Controller Manager+Scheduler+ETCD key value storage)+ Many **Worker Node** (Docker, Container, Apps in worker node, application running) through **Virtual Network** (Turn many machines into one uniformed machine)

### Pod, Service, Ingress

#### Pod

* Smallest unit of K8
* Abstraction over container (Create running environment, a layer that is interacted with)
* Usually 1 application per Pod (Also side services possible)
* Each Pod get IP address and communicate using virtual network
* They can die easily, new one will replace with a new IP address (Can be tiring to change IP each time it changes-->Use Service below)

#### Service

* Permanent IP address attached to each pod
* Lifecycle of Pod and Service NOT connected (Pod die doesn't affect Service)
* External (Public API, HTTP of node IP address + Port number of service) & Internal (Private like database) Service
* Load Balance between nodes

#### Ingress

* Need url be like https://my-app.com instead of https://127.0.0.1:8080 for end product, so that Ingress is needed
* Request goes to Ingress and forward to service

### Config Map and Secret

* Configure DB for application-->DB url is built in application-->New db url, need to rebuild app and push to repo and pull new image into pod (Frustrating!)
* Therefore, **ConfigMap:**
  * External configuration of application
  * Adjust config map and no need to rebuild
  * Don't push credential into Config Map, so use **Secret:**
    * Used to store secret data
    * base64 encoded

### Volumes

* Attach physical storage hard drive to pod, can be local or remote (outside of K8 cluster)

### Deployment Stateful Set

* If application pod dies --> Downtime
* So, replicate everything, replica connected to the service
* Not define a second pod, but define blueprints for pods, define replica numbers
* Pod=Abstraction of Container; Deployment=Abstraction of Pod
* DB cannot be replicated via Deployment: because database has states, so use **StatefulSet**:
  * Take care of replicating pods, and insure database transaction consistency
  * Not easy to do, use DB that is host outside K8 cluster instead

## How to use?

### Minikube and Kubectl

#### Minikube

* One node cluster where master and worker process on ONE machine to test locally
* Run on local machine via Virtual Box

#### Kubectl

* Interact with the cluster created by minikube
* Command line tool for K8 to communicate with Api Server
* Can be also communicate with Cloud clusters

### Install Minikube

* Virtual environment needed -- Hypervisor

### Use Kubectl

* `kubectl get nodes` to get status of minikube clusters
* `kubectl get pod / kubectl get services`
* `kubectl create deployment NAME --image=image [--dry-run] [options]` to create deployment and pods underneath it
* `kubectl logs [pod name] / kubectl describe pod [pod name]` to see logs and status changing regarding the pods
* `kubectl exec -it [pod-name] -- bin/bash` to get into pod's terminal, same as docker exec -it
* `kubectl apply -f [file name]` to use the config file (name.yaml)
  * Sample config file:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
    name: nginx-deployment
    labels:
        app: nginx
spec: // Specification for deployment
    replicas: 1
    selector:
        matchLabels:
            app: nginx
    template:
        metadata:
            labels:
                app: nginx
        spec: // Specification for pods
            containers:
            -   name: nginx
                image: nginx:1.16
                ports:
                -   containerPort: 80
```
