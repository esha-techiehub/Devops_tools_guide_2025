# 4️⃣ Jenkins

## What is Jenkins?

**Layman’s Example:**  
Imagine you run a **bakery 🍞** where customers place orders online:  
1. You get the order  
2. You bake the bread  
3. You pack it  
4. You deliver it  

If you did this manually for every order, it would take forever.  
Instead, you have a **conveyor belt machine** that **automatically bakes, packs, and sends bread** whenever a new order comes in.

That’s **Jenkins** — an **automation server** that automatically **builds, tests, and deploys your code** whenever there’s a change.

**General Definition:**  
Jenkins is an **open-source automation server** used for **Continuous Integration (CI)** and **Continuous Delivery (CD)** — it automates building, testing, and deploying applications.

---

## Why Do We Need Jenkins?

**Without Jenkins:**  
Developers write code → manually send it to testers → manually deploy to servers — **slow** and **error-prone**.

**With Jenkins:**  
The moment code is updated, Jenkins automatically:
1. Pulls the new code from the repository  
2. Builds it  
3. Runs tests  
4. Deploys it to staging/production

---

## Reasons to Use Jenkins
- **Speed** – Automates repetitive development tasks
- **Early Bug Detection** – Tests run on every code change
- **Consistency** – Same process every time
- **Integration** – Works with many tools (Git, Docker, Kubernetes)
- **Flexibility** – Hundreds of plugins for customization

---

## Uses of Jenkins
- Automating code builds  
- Running tests automatically  
- Deploying applications to servers or containers  
- Managing CI/CD pipelines for multiple projects  
- Integrating with cloud platforms for automated releases  

**Example:**  
A ride-sharing app company uses Jenkins so:  
- Every time a developer pushes code to GitHub, Jenkins runs tests  
- If tests pass, Jenkins builds a Docker image  
- Jenkins deploys that image to Kubernetes automatically  

---

## When to Use Jenkins
Use Jenkins if:
- You want CI/CD automation for your development process  
- You have multiple developers working on the same project  
- You release updates frequently  
- You want less manual deployment  

**Not needed if:**  
- You rarely change your app or don’t have an automated test/deployment process  

---

## Jenkins Versions
| Version        | Highlights |
|----------------|------------|
| 1.x (2011–2017) | First stable release, basic CI features |
| 2.x (2017–present) | Pipeline as Code, Blue Ocean UI, better plugins |
| **LTS** | Long Term Support — stable versions updated every 12 weeks |
| **Current (2025)** | 2.452.x LTS ([Check Releases](https://www.jenkins.io/changelog/)) |

---

## Jenkins Terminologies (Layman Examples)

| Term        | Layman Example         | Meaning |
|-------------|------------------------|---------|
| **Job / Project** | One baking order | Task Jenkins performs (build, test, deploy) |
| **Pipeline** | Conveyor belt process | Sequence of automated steps |
| **Build** | Baking the bread | Process of compiling/creating an app |
| **Node** | Bakery branch | Machine where Jenkins runs tasks |
| **Master** | Bakery HQ | Controls and distributes jobs |
| **Agent** | Worker baker | Executes jobs given by master |
| **Plugin** | Extra bakery tool | Adds new features to Jenkins |
| **Workspace** | Kitchen table | Folder where Jenkins stores project files |
| **Trigger** | New customer order | Event that starts a job (push, schedule) |

---

## How to Install Jenkins

### **1. Windows**
Download Jenkins from:  
[https://www.jenkins.io/download/](https://www.jenkins.io/download/)  
Choose `.war` file or Windows installer.

**If using `.war` file:**
```powershell
# Install Java first
java -jar jenkins.war
```
Access Jenkins at:  
[http://localhost:8080](http://localhost:8080)

**If using installer:**  
Just **Next → Next → Finish** and open in browser.

---

### **2. macOS**
```bash
brew install jenkins-lts
brew services start jenkins-lts
```
Access at:  
[http://localhost:8080](http://localhost:8080)

---

### **3. Linux (Ubuntu Example)**
```bash
sudo apt update
sudo apt install openjdk-17-jdk -y

curl -fsSL https://pkg.jenkins.io/debian/jenkins.io-2023.key | sudo tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null

echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null

sudo apt update
sudo apt install jenkins -y
sudo systemctl start jenkins
sudo systemctl enable jenkins
```
Access at:  
`http://your-server-ip:8080`

---

✅ Jenkins is now installed and ready to **automate your CI/CD pipelines**!
