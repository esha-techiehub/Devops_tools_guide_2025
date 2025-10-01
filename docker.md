# Containerization & Docker — Quick Guide (README.md)

This README gives you a practical, interview‑ready and classroom‑friendly overview of **Docker**, **containerization**, the **end‑to‑end workflow**, and a **curated list of common tools** with short explanations and examples.

---

## 1) What is Docker?

**Docker** is a platform for building, shipping, and running applications inside **containers**. It provides:
- **Docker Engine** (`dockerd`) to build & run containers.
- **Docker CLI** (`docker`) to interact with the engine.
- **Docker Desktop** (optional GUI + local VM on Windows/Mac).
- **Dockerfile** format to define how to build images.
- **Images** (read‑only templates) and **containers** (running instances).
- **Registries** (e.g., Docker Hub, GHCR) to store & share images.
- **Volumes** for persistent data and **networks** for container communication.

**Why teams use Docker**
- Same environment everywhere → fewer “works on my machine” issues.
- Faster start‑up vs VMs; lightweight & portable.
- Clean dependency isolation per service.
- Great fit for CI/CD and microservices.

---

## 2) What is Containerization?

**Containerization** is packaging an application **and its dependencies** into a **portable, isolated unit** that runs reliably across different environments. Containers share the **host OS kernel** but keep processes **isolated** using Linux **namespaces** and **cgroups**, and store files with layered/union filesystems (e.g., OverlayFS).

### Containers vs Virtual Machines

| Aspect | Containers | Virtual Machines |
|---|---|---|
| Isolation | Process‑level (namespaces, cgroups) | Hardware‑level (hypervisor) |
| OS | Share host kernel | Full guest OS per VM |
| Footprint | Small, starts in seconds | Larger, slower boot |
| Use cases | Microservices, CI/CD, dev envs | Strong isolation, legacy OS needs |

---

## 3) Containerization Workflow (End‑to‑End)

1. **Plan & scaffold** the app (folder structure, language runtime, ports).
2. **Write a Dockerfile** describing how to build the image.
3. **Build** the image locally or in CI using `docker build` (or BuildKit/Buildx).
4. **Test** the container locally with `docker run` (mount test data if needed).
5. **Scan** the image for vulnerabilities (e.g., `docker scout`, Trivy).
6. **Tag** the image with registry/repo name and version.
7. **Push** the image to a **registry** (Docker Hub, GHCR, ECR, ACR, GAR/GCR, Harbor).
8. **Deploy/Run** the container in your target env (VM, server, Kubernetes, ECS, AKS, etc.).
9. **Observe** (logs, metrics), **update** (rebuild/tag/push), and **roll back** if needed.

### Example: Minimal Dockerfile (Python FastAPI)
```dockerfile
# syntax=docker/dockerfile:1
FROM python:3.12-slim

# Create app dir, install deps
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy source and run
COPY . .
EXPOSE 8000
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

**Build & run:**
```bash
# 1) Build
docker build -t myorg/fastapi-demo:1.0.0 .

# 2) Test locally
docker run --rm -p 8000:8000 myorg/fastapi-demo:1.0.0

# 3) (Optional) Scan
docker scout cves myorg/fastapi-demo:1.0.0

# 4) Push to a registry
docker login
docker push myorg/fastapi-demo:1.0.0
```

### Example: `docker-compose.yml` (local multi‑service dev)
```yaml
version: "3.9"
services:
  api:
    build: .
    ports:
      - "8000:8000"
    env_file: .env
    depends_on:
      - db
  db:
    image: postgres:16
    environment:
      POSTGRES_USER: app
      POSTGRES_PASSWORD: secret
      POSTGRES_DB: appdb
    volumes:
      - pgdata:/var/lib/postgresql/data
volumes:
  pgdata:
```

**Run:** `docker compose up --build`

---

## 4) Common Containerization Tools (with short explanations)

### A) Engines & Runtimes (build/run containers)
- **Docker Engine** — The most widely used container engine; includes BuildKit, networking, volumes, and Docker CLI.
- **containerd** — CNCF project (extracted from Docker), a daemon used by Kubernetes; `nerdctl` is the Docker‑like CLI for it.
- **CRI‑O** — Kubernetes‑focused runtime implementing the CRI (Container Runtime Interface), often used on Red Hat/OKD/OpenShift.
- **Podman** — Daemonless container engine from Red Hat; CLI mostly compatible with Docker. Can run **rootless** containers and generate systemd units.
- **LXC/LXD** — System containers (closer to lightweight VMs) with broader OS management; good for long‑running system services.

### B) Builders (create images)
- **Docker Buildx / BuildKit** — Next‑gen Docker builder (multi‑platform, cache exports, advanced features).
- **Buildah** — Build OCI images without a daemon; pairs well with Podman.
- **Kaniko** — Build images **inside** a container without privileged Docker (great for CI in Kubernetes).
- **Jib (Java)** — Builds container images for Java apps **without** a Dockerfile, integrating with Maven/Gradle.
- **Cloud Native Buildpacks (pack, buildpacks.io)** — Detects language, builds images from source automatically (Heroku/Paas‑style).

### C) Developer Workflow Helpers
- **Docker Compose** — Define/run multi‑container apps locally via YAML (great for dev/test).
- **Skaffold** — Google tool to build, sync, and deploy to Kubernetes for fast inner‑loop dev.
- **Tilt** — Live‑reload local‑to‑Kubernetes dev tool; watches source and updates pods quickly.
- **minikube / kind** — Local Kubernetes clusters to test deployments.

### D) Orchestrators (not “containerizers” but essential in prod)
- **Kubernetes** — Standard for container orchestration (scheduling, scaling, rolling updates, services/ingress).
- **Docker Swarm** — Simpler orchestrator bundled with Docker; less common today than Kubernetes.

### E) Registries (store & distribute images)
- **Docker Hub** — Public registry with free/private repos.
- **GitHub Container Registry (GHCR)** — Integrated with GitHub; great for Actions workflows.
- **GitLab Container Registry** — Built into GitLab; tight CI/CD integration.
- **Amazon ECR / Azure ACR / Google GAR|GCR** — Managed cloud registries for AWS, Azure, and GCP.
- **Harbor** — Open‑source enterprise registry with vulnerability scanning, replication, RBAC.

> **Tip:** All of the above speak **OCI** (Open Container Initiative) images, so they interoperate smoothly.

---

## 5) Best Practices (Quick Checklist)

- Use **small base images** (`alpine`, `-slim`) and **multi‑stage builds** to keep images tiny.
- Run as a **non‑root** user; drop Linux capabilities when possible.
- Keep **one process per container**; scale by adding replicas.
- Store config in **env vars** / secrets, not in the image.
- Use **.dockerignore** to exclude junk from build context.
- Pin versions & verify checksums for deterministic builds.
- Scan images regularly (Trivy, Docker Scout, Harbor scanners).
- Use **healthchecks**, proper signals, and graceful shutdown.
- Log to **stdout/stderr**; let the platform collect logs.
- Automate builds & pushes in **CI/CD**; tag with semantic versions and immutable digests.

---

## 6) Troubleshooting (Basics)

- **Container exits immediately** → Is your process foregrounded? Check `CMD/ENTRYPOINT` and logs via `docker logs <id>`.
- **Port not reachable** → Map ports with `-p host:container`, verify the app binds to `0.0.0.0`, check firewall/SG rules.
- **Permission denied** → Volume ownership/UID mismatch; run as correct user or adjust `chown`, avoid root.
- **Huge images** → Enable multi‑stage builds, switch to `-slim` base, clean caches (`--no-cache-dir`, `rm -rf /var/cache/...`).
- **Slow builds** → Use BuildKit, cache deps, optimize layer order (change less‑often layers first).

---

## 7) Quick Glossary

- **Image**: Read‑only template with app + dependencies (layers).
- **Container**: Running instance of an image.
- **Registry**: Remote store for images (push/pull).
- **Tag**: Human‑readable version label (e.g., `1.0.0`).
- **Digest**: Immutable image content hash (e.g., `@sha256:...`).
- **Volume**: External persistent storage for a container.
- **OverlayFS**: Union filesystem that stacks layers efficiently.
- **Namespace / cgroup**: Kernel features for isolation & resource control.
- **OCI**: Open standards for images and runtimes.

---

## 8) Quick Start Commands

```bash
# Check versions / status
docker version
docker info

# Build and run
docker build -t demo/app:1.0.0 .
docker run --rm -p 8080:80 demo/app:1.0.0

# List images/containers
docker images
docker ps -a

# Publish
docker tag demo/app:1.0.0 ghcr.io/myorg/app:1.0.0
docker login ghcr.io
docker push ghcr.io/myorg/app:1.0.0
```

---

## 9) Suggested Folder Layout
```
.
├─ Dockerfile
├─ docker-compose.yml        # optional (local dev)
├─ .dockerignore
├─ requirements.txt / package.json / pom.xml
└─ src/                      # your app code
```

---

### ✅ Use this README in your repo root as `README.md`. 
Feel free to customize the Dockerfile example and the toolset sections for your stack (Python/Node/Java, cloud provider, CI system).
