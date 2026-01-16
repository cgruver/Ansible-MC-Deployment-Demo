# Ansible MC Deployment Demo

This repository contains Ansible playbooks and roles used to deploy and configure a vanilla Minecraft server. The demo supports both traditional VM-based deployments and OpenShift-based deployments using Kubernetes APIs.

The intent of this repository is to demonstrate how Ansible can be used to automate application configuration and container platform deployments in a repeatable, infrastructure-as-code workflow.

---

## Prerequisites

- Ansible installed on the control node
- Access to the target VM or OpenShift cluster
- OpenShift CLI (`oc`) installed and configured
- Appropriate permissions to deploy workloads in the target environment

---

## Environment Authentication

Authentication to the Kubernetes or OpenShift API is handled using environment variables.

When targeting OpenShift, export the API token directly from the active `oc` session:

Ensure you are logged into the cluster before setting these variables:

```bash
oc login
```

```bash
export K8S_AUTH_API_KEY="$(oc whoami -t)"
export K8S_AUTH_HOST="https://api.<cluster-name>.<domain>:6443"
```

## Running the Playbook

### Configure Minecraft on a VM
This playbook prepares and configures a Minecraft server on a virtual machine:

```yaml
ansible-playbook -i inventory minecraft-vm-deploy.yml
```

### Deploy Minecraft to OpenShift
This playbook deploys Minecraft into an OpenShift cluster using Kubernetes resources:
```yaml
ansible-playbook minecraft-oc-deploy.yml
```

## Purpose

This repository serves as a demonstration of:
- Infrastructure automation with Ansible
- Application deployment consistency
- Kubernetes and OpenShift API-driven workflows
- Portable automation patterns for both VM and container platforms