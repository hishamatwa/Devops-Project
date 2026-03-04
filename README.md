# Devops-Project
# DevOps Project — Voting App Automation

This is a DevOps automation project to deploy the **Voting App microservices** on a local Kubernetes cluster (**kind**). It uses **Kubernetes manifests** and **Ansible** to deploy, verify, and cleanup the application.

## ✨ What this project can do
- 🚀 Deploy the full app with one command (Ansible)
- ✅ Verify pods, services, and endpoints
- 🧹 Cleanup (delete app resources and namespace)
- 📄 Provide simple documentation + a short security review

## 🧩 Microservices
- vote: voting web page
- redis: temporary votes store
- worker: moves votes from redis to db
- db (PostgreSQL): stores results
- result: results web page

## 🚀 How to Run

### 1) Create the local Kubernetes cluster
```bash
kind create cluster --image kindest/node:v1.29.7
kubectl get nodes
