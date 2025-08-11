# 1️⃣ Kubernetes

## What is Kubernetes?

**Layman’s Example:**  
Imagine you own a big chain of restaurants 🍔. You have multiple chefs (servers) cooking food (running apps), and you need a manager who:
- Makes sure there’s always enough chefs for the crowd
- Moves chefs between branches if needed
- Hires new ones automatically if there’s a rush
- Fires extra chefs if it’s quiet

That manager is **Kubernetes** — it takes care of deploying, scaling, and managing your applications automatically.

**General Definition:**  
Kubernetes (aka **K8s**) is an **open-source container orchestration platform** that automates deploying, scaling, and operating applications in containers.

---

## Why Do We Need Kubernetes?

**Without Kubernetes:**  
You have to manually start/stop containers, monitor if they crash, restart them, and balance the load.

**With Kubernetes:**  
It automates all of that — like an **autopilot for containers**.

**Reasons to Use Kubernetes:**
- Handles scaling (more/less containers depending on demand)
- Automatically restarts crashed apps
- Load balances traffic to healthy apps
- Runs apps across multiple machines easily
- Works with different cloud providers or even your own data center

---

## Uses of Kubernetes
- Hosting microservices-based applications
- Running machine learning workloads
- Deploying and scaling APIs/web apps
- Managing batch jobs
- Hybrid cloud application deployments

**Example:**  
An e-commerce site uses Kubernetes to make sure:
- Web frontend always has enough instances during sales
- Database connections are stable
- If a server crashes, it replaces it instantly

---

## When to Use Kubernetes
Use Kubernetes if:
- You have lots of containers and need to manage them at scale
- You want high availability for your apps
- You need auto-scaling based on traffic
- You want your app to run on multiple clouds without changes
- Your infrastructure changes often, and you need automation

**Not needed if:**
- You have only 1-2 containers and don’t need scaling

---

## Kubernetes Versions
| Version | Highlights |
|---------|------------|
| 1.0 (2015) | First stable release by Google |
| 1.6 – 1.9 | RBAC, stateful sets improvements |
| 1.14 | Windows container support |
| 1.16 – 1.18 | Major API changes |
| 1.20 – 1.22 | Deprecations and stable features |
| Current (2025) | ~1.31.x (check [Kubernetes Release Notes](https://kubernetes.io/releases/)) |

---

## Kubernetes Terminologies (Layman Examples)

| Term       | Layman Example                   | Meaning |
|------------|----------------------------------|---------|
| **Cluster** | Your entire chain of restaurants | Group of machines running Kubernetes |
| **Node**    | One restaurant branch            | A single machine (VM or physical) |
| **Pod**     | Kitchen with 1 or more chefs     | Smallest deployable unit with containers |
| **Container** | The chef cooking a specific dish | Application package with dependencies |
| **Deployment** | Hiring plan for chefs          | Blueprint for running pods |
| **Service** | Waiters directing customers to kitchens | Way to expose pods and balance traffic |
| **Namespace** | Separate section in a big mall | Logical grouping of resources |
| **Ingress** | Front door & menu board          | Manages external access to services |
| **ConfigMap** | Recipe book                    | Stores configuration data |
| **Secret**  | Safe locker for secret ingredients | Stores sensitive data like passwords |

---

## How to Install Kubernetes (K8s)

### **1. Windows (Using Minikube for Local Learning)**
1. Install **Docker Desktop** ([Download](https://www.docker.com/products/docker-desktop/))
2. Install **Chocolatey** (package manager):
   ```powershell
   Set-ExecutionPolicy Bypass -Scope Process -Force; `
   [System.Net.ServicePointManager]::SecurityProtocol = `
   [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; `
   iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
   ```
3. Install Minikube:
   ```powershell
   choco install minikube
   ```
4. Start Minikube:
   ```powershell
   minikube start
   ```
5. Verify:
   ```powershell
   kubectl get nodes
   ```

---

### **2. macOS**
```bash
brew install minikube
minikube start
kubectl get nodes
```

---

### **3. Linux (Ubuntu Example)**
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
minikube start
kubectl get nodes
```

---

✅ You now have a running **local Kubernetes cluster** for learning and testing!
