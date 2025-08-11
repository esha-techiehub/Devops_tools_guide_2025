# 2️⃣ Docker

## What is Docker?

**Layman’s Example:**  
Imagine you’re a chef 🍳 who has to cook the same dish in many different kitchens.  
Normally, you’d have problems — some kitchens don’t have the same stove, spices, or utensils.  
So instead, you carry a **cooking box 🧰** with everything you need — ingredients, utensils, recipe — so you can cook exactly the same dish anywhere.

That cooking box is **Docker** — it packages your application with all its dependencies so it can run anywhere without “it works on my computer” problems.

**General Definition:**  
Docker is an **open-source platform** that lets you package, distribute, and run applications in **containers**, ensuring **consistency across different environments**.

---

## Why Do We Need Docker?

**Without Docker:**  
You develop an app on your laptop, it works fine. Then on the server, it breaks because the software versions, dependencies, or configurations are different.

**With Docker:**  
You put your app inside a **container** with everything it needs. Wherever you run it — laptop, server, or cloud — it works the same.

---

## Reasons to Use Docker
- **Portability** – Runs anywhere (Windows, Linux, Mac, Cloud)
- **Consistency** – Same environment everywhere
- **Isolation** – Each app runs in its own container
- **Faster Deployment** – No need to set up dependencies each time
- **Easy Scaling** – Run multiple containers quickly

---

## Uses of Docker
- Packaging and shipping software easily
- Running microservices in isolated containers
- Testing different versions of software quickly
- Creating reproducible development environments
- Supporting Continuous Integration / Continuous Deployment (CI/CD)

**Example:**  
A payment gateway company uses Docker so:
- Developers can code locally in the same environment as production
- QA testers can test the exact same setup as production
- Deployment takes minutes instead of hours

---

## When to Use Docker
Use Docker if:
- You want your app to run identically everywhere
- You have multiple apps needing different dependencies
- You need fast scaling of apps in the cloud
- You’re building microservices architecture

**Not needed if:**
- You’re just running one app on one machine with no scaling or environment issues

---

## Docker Versions
| Version         | Highlights |
|-----------------|------------|
| 1.x (2013–2017) | Initial release, CLI improvements |
| 17.x (2017)     | Versioning change (YY.MM format) |
| 18.x – 19.x     | Better networking & orchestration |
| 20.x – 23.x     | Security, performance upgrades |
| Current (2025)  | ~25.x (check [Docker Releases](https://docs.docker.com/release-notes/)) |

---

## Docker Terminologies (Layman Examples)

| Term          | Layman Example                  | Meaning |
|---------------|---------------------------------|---------|
| **Image**     | A cooking recipe + ingredients  | Blueprint for creating containers |
| **Container** | The actual meal cooked from the recipe | Running instance of an image |
| **Dockerfile**| Written recipe                   | Instructions to build an image |
| **Docker Hub**| Recipe store (like YouTube for images) | Public registry for images |
| **Volume**    | Fridge for storing leftovers     | Persistent storage for containers |
| **Network**   | Phone lines between kitchens     | Communication between containers |
| **Bind Mount**| Sharing your home fridge         | Mapping local folders to containers |
| **Port Mapping**| Restaurant front door number   | Exposing container’s service to outside |
| **Registry**  | Recipe book storage place        | Storage for images (public or private) |

---

## How to Install Docker

### **1. Windows**
1. Download **Docker Desktop**: [Download Here](https://www.docker.com/products/docker-desktop/)  
2. Install like normal software (**Next → Next → Finish**).  
3. After installation, open **PowerShell** and check version:
   ```powershell
   docker --version
   ```
4. Run a test container:
   ```powershell
   docker run hello-world
   ```

---

### **2. macOS**
```bash
brew install --cask docker
open /Applications/Docker.app
docker --version
docker run hello-world
```

---

### **3. Linux (Ubuntu Example)**
```bash
sudo apt-get update
sudo apt-get install ca-certificates curl gnupg lsb-release
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
docker --version
docker run hello-world
```

---

✅ You now have **Docker installed** and can start running containers!
