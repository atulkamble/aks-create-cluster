<div align="center">
<h1>🚀 AKS Create Cluster</h1>
<p><strong>Built with ❤️ by <a href="https://github.com/atulkamble">Atul Kamble</a></strong></p>

<p>
<a href="https://codespaces.new/atulkamble/template.git">
<img src="https://github.com/codespaces/badge.svg" alt="Open in GitHub Codespaces" />
</a>
<a href="https://vscode.dev/github/atulkamble/template">
<img src="https://img.shields.io/badge/Open%20with-VS%20Code-007ACC?logo=visualstudiocode&style=for-the-badge" alt="Open with VS Code" />
</a>
<a href="https://vscode.dev/redirect?url=vscode://ms-vscode-remote.remote-containers/cloneInVolume?url=https://github.com/atulkamble/template">
<img src="https://img.shields.io/badge/Dev%20Containers-Ready-blue?logo=docker&style=for-the-badge" />
</a>
<a href="https://desktop.github.com/">
<img src="https://img.shields.io/badge/GitHub-Desktop-6f42c1?logo=github&style=for-the-badge" />
</a>
</p>

<p>
<a href="https://github.com/atulkamble">
<img src="https://img.shields.io/badge/GitHub-atulkamble-181717?logo=github&style=flat-square" />
</a>
<a href="https://www.linkedin.com/in/atuljkamble/">
<img src="https://img.shields.io/badge/LinkedIn-atuljkamble-0A66C2?logo=linkedin&style=flat-square" />
</a>
<a href="https://x.com/atul_kamble">
<img src="https://img.shields.io/badge/X-@atul_kamble-000000?logo=x&style=flat-square" />
</a>
</p>

<strong>Version 1.0.0</strong> | <strong>Last Updated:</strong> January 2026
</div>

---

# 🚀 AKS Create Cluster

**Create and manage an Azure Kubernetes Service (AKS) cluster using Azure CLI**
Designed for **DevOps engineers, cloud architects, and learners**.

---

![Image](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/containers/aks-microservices/images/microservices-architecture.svg)

![Image](https://learn.microsoft.com/en-us/azure/architecture/reference-architectures/containers/aks/images/tls-termination.svg)

![Image](https://learn.microsoft.com/en-us/azure/architecture/example-scenario/aks-dualstack/images/dual-stack-inline.png)

![Image](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/scenarios/app-platform/aks/media/network-private-cluster.png)

## 📌 Overview

This repository provides **step-by-step instructions** to create an **AKS (Azure Kubernetes Service) cluster** using **Azure CLI**, including:

* Resource Group creation
* AKS Cluster provisioning
* Node pool configuration
* `kubectl` access
* Cluster validation
* Basic post-deployment checks

✅ Ideal for **POCs**, **training labs**, and **production-ready foundations**

---

## 🏗️ Architecture

**High-level AKS Architecture**

```
Azure Subscription
│
├── Resource Group
│   ├── AKS Cluster
│   │   ├── Control Plane (Managed by Azure)
│   │   ├── System Node Pool
│   │   └── User Node Pool
│   │
│   ├── Virtual Network (VNet)
│   ├── Subnets
│   └── Load Balancer
│
└── Azure Container Registry (Optional)
```

---

## 🔧 Prerequisites

Ensure the following are installed and configured:

* ✅ Azure Subscription
* ✅ Azure CLI (`az`)
* ✅ kubectl
* ✅ Valid Azure login

### Install Azure CLI

```bash
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```

### Login to Azure

```bash
az login
```

---

## 📁 Repository Structure

```
aks-create-cluster/
├── README.md
├── scripts/
│   ├── 01-resource-group.sh
│   ├── 02-aks-create.sh
│   └── 03-get-credentials.sh
└── docs/
    └── architecture.md
```

---

## 🚀 Step-by-Step AKS Cluster Creation

### 1️⃣ Create Resource Group

```bash
az group create \
  --name aks-rg \
  --location eastus
```

---

### 2️⃣ Create AKS Cluster

```bash
az aks create \
  --resource-group aks-rg \
  --name aks-demo-cluster \
  --node-count 2 \
  --node-vm-size Standard_DS2_v2 \
  --enable-managed-identity \
  --generate-ssh-keys
```

⏱️ **Provisioning Time:** ~5–10 minutes

---

### 3️⃣ Get AKS Credentials

```bash
az aks get-credentials \
  --resource-group aks-rg \
  --name aks-demo-cluster
```

Verify:

```bash
kubectl get nodes
```

---

## ✅ Validation & Testing

```bash
kubectl cluster-info
kubectl get nodes -o wide
kubectl get pods -A
```

Expected Output:

* Nodes in **Ready** state
* System pods running in `kube-system`

---

## 🔐 Security Best Practices

* Use **Managed Identity** (enabled by default)
* Integrate **Azure AD** for RBAC
* Restrict API server access
* Use **Network Policies**
* Enable **Azure Monitor & Defender for AKS**

---

## 📈 Production Enhancements (Optional)

* 🔹 Enable Auto Scaling
* 🔹 Add User Node Pools
* 🔹 Attach Azure Container Registry (ACR)
* 🔹 Enable Azure Monitor
* 🔹 Configure Ingress Controller (NGINX)

---

## 🧹 Cleanup (Avoid Extra Costs)

```bash
az group delete \
  --name aks-rg \
  --yes --no-wait
```

---

## 📚 Useful Commands Cheat Sheet

```bash
kubectl get nodes
kubectl get svc
kubectl get deployments
kubectl describe node <node-name>
```

---

## 🎯 Use Cases

* DevOps CI/CD Pipelines
* Microservices Deployment
* Kubernetes Training & Labs
* Cloud-Native Application Hosting

---

## 🤝 Contributing

Contributions are welcome!

1. Fork the repo
2. Create a feature branch
3. Commit changes
4. Open a Pull Request

---

## 📄 License

This project is licensed under the **MIT License**.

---

## 👨‍💻 Author

**Atul Kamble**
Cloud & DevOps Architect | Trainer | Founder

🔗 GitHub: [https://github.com/atulkamble](https://github.com/atulkamble)

---
