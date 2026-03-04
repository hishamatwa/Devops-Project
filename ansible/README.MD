# Ansible Automation

This folder contains Ansible files to run the Voting App on Kubernetes.

## What is inside
- `inventory.ini`  
  Tells Ansible to run on the same machine (localhost).

- `deploy.yml`  
  Deploys the app (creates the namespace and applies Kubernetes files).

- `verify.yml`  
  Checks if the app is running (pods, services, and endpoints).

- `cleanup.yml`  
  Removes the app and deletes the namespace (safe to run many times).

If you want the full steps, check the main README in the repository root.
