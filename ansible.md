# 3️⃣ Ansible

## What is Ansible?

**Layman’s Example:**  
Imagine you own **100 houses 🏠** in different cities, and you need to:  
- Install air conditioners  
- Paint the walls blue  
- Fix the lights  

If you do this **house by house**, it will take forever.  
Instead, you write a **to-do list 📋** and give it to a **team leader**, who sends the same instructions to all houses at once — job done in minutes.

That’s **Ansible** — it sends instructions to **multiple machines at once** to configure them exactly how you want.

**General Definition:**  
Ansible is an **open-source automation tool** used for **configuration management**, **application deployment**, and **task automation** across multiple systems, using **simple text files (YAML)**.

---

## Why Do We Need Ansible?

**Without Ansible:**  
If you have 50 servers, you log into each one and manually install, configure, and update software — slow and error-prone.

**With Ansible:**  
You write a **playbook** (instruction file) once, and Ansible runs it on **all servers at the same time** — fast, consistent, and no mistakes.

---

## Reasons to Use Ansible
- **Saves Time** – Automates repetitive tasks
- **No Special Agent Needed** – Works over SSH
- **Consistent** – Same setup everywhere
- **Simple Language** – Uses YAML, easy to read
- **Cross-Platform** – Works on Linux, Windows, Cloud

---

## Uses of Ansible
- Installing software on multiple servers
- Configuring servers with correct settings
- Deploying applications automatically
- Managing updates and security patches
- Orchestrating multi-server setups (e.g., load balancers + app servers + databases)

**Example:**  
An online learning platform uses Ansible to:
- Install MySQL on all database servers
- Configure Nginx on all web servers
- Deploy new code to all servers with **one command**

---

## When to Use Ansible
Use Ansible if:
- You manage multiple machines that need the same setup
- You need quick deployments and updates
- You want to avoid manual configuration mistakes
- You’re setting up complex infrastructure repeatedly

**Not needed if:**
- You only have 1–2 machines and change settings rarely

---

## Ansible Versions
| Version          | Highlights |
|------------------|------------|
| 1.x (2012–2015)  | First stable versions |
| 2.0 – 2.9        | Major improvements & modules added |
| 2.10 – 4.x       | Moved to “Collections” model |
| 5.x – 8.x        | Performance & security improvements |
| Current (2025)   | Ansible Core 2.17.x / Ansible 9.x ([Check Releases](https://docs.ansible.com/ansible/latest/roadmap/ROADMAP_2_17.html)) |

---

## Ansible Terminologies (Layman Examples)

| Term           | Layman Example                        | Meaning |
|----------------|---------------------------------------|---------|
| **Playbook**   | Recipe book for all houses            | YAML file with tasks to run |
| **Task**       | One step in the recipe                | Single action Ansible will perform |
| **Role**       | Pre-made recipe set                   | Organized way to group playbooks & tasks |
| **Inventory**  | Address list of all houses            | List of servers Ansible will manage |
| **Module**     | Tool in your toolbox                  | Predefined function (e.g., install package) |
| **Handler**    | Cleaner who acts after a task         | Runs only when triggered by changes |
| **Facts**      | Information about the house           | System details collected before tasks |
| **Idempotency**| Painting the wall blue only if not already blue | Ensures repeated runs don’t break things |
| **Ad-hoc Command** | Calling plumber directly          | Quick one-time command without a playbook |

---

## How to Install Ansible

### **1. Windows**
Ansible doesn’t run natively on Windows, but you can:  
- Use **Windows Subsystem for Linux (WSL)** to run Ansible  
- Or run Ansible from a **Linux VM** controlling Windows servers

**WSL Installation:**
```powershell
wsl --install
```
Install **Ubuntu** from Microsoft Store. Inside Ubuntu:
```bash
sudo apt update
sudo apt install ansible -y
ansible --version
```

---

### **2. macOS**
```bash
brew install ansible
ansible --version
```

---

### **3. Linux (Ubuntu Example)**
```bash
sudo apt update
sudo apt install ansible -y
ansible --version
```

---

✅ Now you have **Ansible installed** and ready to automate your infrastructure!
