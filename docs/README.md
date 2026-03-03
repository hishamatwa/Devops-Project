# Voting App - Local Deployment Automation (Docker + Kubernetes/kind + Ansible)

## What is this project?
This repository provides deployment automation for the Voting App reference microservices on a local Kubernetes cluster (kind) using Ansible.
The goal is a clean and repeatable deployment (one command).

## Services (microservices)
- vote: web UI for voting
- redis: temporary storage for votes
- worker: processes votes and writes to the database
- db (PostgreSQL): stores results
- result: web UI to display results

All resources run in the Kubernetes namespace: `voting-app`.

---

## Reference source (GitHub)
The application is based on the public repository: `nexusameer/Voting-App-Microservices`.
This work focuses on Kubernetes deployment, automation, verification, and documentation.

---

## Tools used (only)
- Linux (RHEL VM)
- Docker
- Kubernetes: kind + kubectl
- Ansible

No cloud provider and no Terraform are used.

---

## Versions used (my environment)
- Docker: 29.2.1 (build a5c7197)
- kubectl (client): v1.29.7
- kind: v0.32.0-alpha+c62c35f841826f
- Ansible core: 2.15.13
- Python: 3.11.13
- Kubernetes node image for kind: kindest/node:v1.29.7

---

## Folder structure
- kubernetes/namespace.yaml : creates namespace `voting-app`
- kubernetes/app/ : Kubernetes manifests (Deployments + Services)
- ansible/inventory.ini : local inventory (runs on this VM)
- ansible/deploy.yml : one-command deployment automation
- docs/ : documentation

---

## Network / Ports
### Internal service names (inside Kubernetes)
- db:5432
- redis:6379
- vote:8080  (service port)
- result:8081 (service port)

### Open the web pages (recommended: port-forward)
Because kind is local, LoadBalancer external IP may stay `<pending>`.
Port-forward is the safest way.

Vote UI:
```bash
kubectl -n voting-app port-forward svc/vote 18080:8080
