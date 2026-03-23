# 📘 GitOps Flow – Notes

## 🚀 What is GitOps?

**GitOps** is a way of managing infrastructure and applications using Git as the **single source of truth**.
All changes are made through Git commits, and systems automatically sync those changes to the cluster.

A popular tool used for GitOps is Argo CD.

---

## 📦 Manifests Repository

The Kubernetes manifests used in this project are stored in the following Git repository:

🔗 [GitHub Repository](https://github.com/OmkarNampalli/CI-CD-using-Github-Actions/tree/main/K8s-manifests)

---

## 🔁 GitOps Flow (Step-by-Step)

### 1. Developer Makes Changes

* Developer updates application code or Kubernetes manifests (YAML files)
* Changes are pushed to a Git repository (e.g., GitHub)

---

### 2. Git Repository Stores Desired State

* Git contains:

  * Deployment configs
  * Services
  * ConfigMaps, Secrets (optional)
* This represents the **desired state** of the system

---

### 3. GitOps Tool Watches Repository

* Tools like Argo CD continuously monitor the repo
* Detects any new commits or changes

---

### 4. Compare Desired vs Actual State

* GitOps tool compares:

  * **Desired state (Git)**
  * **Actual state (Kubernetes cluster)**

---

### 5. Sync Changes to Cluster

* If differences are found:

  * Tool automatically applies changes using `kubectl`
* This ensures the cluster always matches Git

---

### 6. Continuous Reconciliation

* Even if someone manually changes the cluster:

  * GitOps tool will revert it back to match Git

---

## 🔄 Flow Diagram (Simple)

```
Developer → Git Repo → Argo CD → Kubernetes Cluster
                ↑             ↓
            Desired State   Actual State
```

---

## 🧩 Key Components

### 📁 Git Repository

* Stores all configurations
* Version-controlled
* Acts as the **single source of truth**

---

### ⚙️ GitOps Controller

* Example: Argo CD
* Responsibilities:

  * Monitor Git
  * Detect changes
  * Sync with cluster

---

### ☸️ Kubernetes Cluster

* Where applications run
* Can be local (e.g., Minikube) or cloud

---

## ✅ Benefits of GitOps

* 🔍 **Version Control** – All changes tracked in Git
* 🔄 **Automatic Deployment** – No manual kubectl commands
* 🔐 **Auditability** – Full history of changes
* ⚡ **Quick Rollbacks** – Revert to previous commit
* 🤖 **Self-Healing** – Cluster auto-corrects drift

---

## ⚠️ Important Concepts

### Desired State

* Defined in Git (YAML files)

### Actual State

* Running state in Kubernetes

### Drift

* When actual state ≠ desired state

---

## 🧪 Example Workflow

1. Update `deployment.yaml`
2. Commit & push to Git
3. Argo CD detects change
4. Syncs new config to cluster
5. Application updates automatically

---

## 🔐 Best Practices

* Use separate repos for:

  * App code
  * Kubernetes manifests
* Protect main branch (PR approvals)
* Avoid manual cluster changes
* Use secrets management tools

---

## 🧠 Summary

GitOps =
👉 **Git as source of truth**
👉 **Automated deployments**
👉 **Continuous reconciliation**

---

## 🎯 Final Thought

GitOps simplifies deployments by making Git the control center of your system.
Once set up, tools like Argo CD handle everything automatically, ensuring consistency and reliability.

---
