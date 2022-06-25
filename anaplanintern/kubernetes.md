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
