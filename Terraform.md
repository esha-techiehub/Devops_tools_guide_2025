# Terraform Documentation

## 1️⃣ What is Terraform?

**Layman’s Example:**  
Think of Terraform like a **remote control for your cloud**.  
Instead of logging into AWS, Azure, or GCP manually and clicking buttons to create servers, networks, and databases, Terraform lets you write everything in a script and press one button to create them all automatically.

**General Definition:**  
Terraform is an **Infrastructure as Code (IaC)** tool developed by **HashiCorp** that allows you to define, provision, and manage cloud infrastructure using code instead of manual processes.

---

## 2️⃣ Why Use Terraform?

**Without Terraform:**  
It’s like building a house by hand every time — measuring, cutting, and hammering yourself. Time-consuming, repetitive, and prone to mistakes.

**With Terraform:**  
It’s like having a **blueprint** — every time you want a house, you give the blueprint to a construction robot, and it builds it exactly the same way every time.

**Benefits:**
- **Automation** – No more manual clicking in cloud consoles.
- **Consistency** – Recreate the exact same environment anytime.
- **Multi-cloud Support** – Works with AWS, Azure, GCP, VMware, and more.
- **Version Control** – Track infrastructure changes like software code.
- **Scalability** – Create hundreds of resources quickly and reliably.

---

## 3️⃣ Uses of Terraform

**General Uses:**
- Creating and managing cloud infrastructure (servers, networks, databases, storage).
- Automating repetitive cloud setup tasks.
- Managing configurations for different environments (dev, test, prod).
- Quickly replicating infrastructure for different clients or teams.
- Disaster recovery — recreate environments after a crash.

**Example:**  
Imagine you run a food delivery startup. You need:
- A web server
- A database
- Storage for images

Terraform can set up all of this in **one go** instead of doing it manually.

---

## 4️⃣ When to Use Terraform

You should use Terraform when:
- You have **many resources** to set up in the cloud.
- You **repeat the same setups** (like dev, test, and prod environments).
- You want to manage **multiple cloud providers** with one tool.
- You need **disaster recovery** or **quick redeployment**.
- You want to **track changes** to infrastructure.

**Example:**  
If you only need 1 small server once, manual setup might be fine.  
But if you need **20 servers + networking + databases** across AWS & Azure — Terraform saves hours.

---

## 5️⃣ Terraform Versions

| Version Range     | Highlights |
|-------------------|------------|
| 0.11 and below    | Old syntax, rarely used today |
| 0.12 (2019)       | Big syntax improvements |
| 0.13 – 0.14       | Module improvements, better workflows |
| 0.15              | More stability |
| 1.x               | Stable production releases (current ~1.9.x as of 2025) |

> 💡 **Tip:** Always check [Terraform Official Releases](https://developer.hashicorp.com/terraform/downloads) for the latest version.

---

## 6️⃣ Terraform Terminologies (with Layman Examples)

| Term       | Layman Example                        | Meaning in Terraform |
|------------|---------------------------------------|----------------------|
| **Provider** | The company/store you buy from (e.g., Amazon, Flipkart) | The cloud/service provider (AWS, Azure, GCP) Terraform interacts with. |
| **Resource** | An item you order (TV, sofa)         | The actual cloud component (EC2, S3 bucket, VM). |
| **Module**   | A pre-packed furniture set           | A collection of Terraform files you can reuse. |
| **State File**| Receipt of what you bought          | Tracks the infrastructure Terraform has created. |
| **Plan**     | Shopping list before you buy         | Shows what Terraform will create, change, or delete. |
| **Apply**    | Buying the items                     | Executes the plan and provisions infrastructure. |
| **Destroy**  | Selling everything you bought        | Removes all the infrastructure you created. |
| **Variable** | Sizes/colors you choose for items    | Custom values to make Terraform code flexible. |
| **Output**   | Delivery tracking number             | Information Terraform shows after deployment. |

---

## 7️⃣ Installing Terraform

### Step 1: Check if Terraform is Installed
Open your terminal and run:
```bash
terraform -version

##** 8. Installation Steps**

### **Windows**
1. Go to [Terraform Downloads](https://developer.hashicorp.com/terraform/downloads).
2. Download the latest **Windows** version (ZIP file).
3. Extract the ZIP file to a folder (example: `C:\terraform`).
4. Add the folder path to **Environment Variables**:
   - Press `Windows + S` → search for **Environment Variables**.
   - Edit **Path** → Add `C:\terraform`.
5. Open **Command Prompt** or **PowerShell** and verify:
   ```bash
   terraform -version
   ```

---

### **macOS**
1. Install using **Homebrew**:
   ```bash
   brew tap hashicorp/tap
   brew install hashicorp/tap/terraform
   ```
2. Verify installation:
   ```bash
   terraform -version
   ```

---

### **Linux (Ubuntu/Debian)**
1. Update and install dependencies:
   ```bash
   sudo apt-get update && sudo apt-get install -y gnupg software-properties-common curl
   ```
2. Add HashiCorp GPG key:
   ```bash
   curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
   ```
3. Add official HashiCorp repo:
   ```bash
   echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
   ```
4. Install Terraform:
   ```bash
   sudo apt-get update && sudo apt-get install terraform
   ```
5. Verify:
   ```bash
   terraform -version
   ```

---

## 4. Verify Installation
Run:
```bash
terraform -version
```
Example output:
```
Terraform v1.9.5
on linux_amd64
```

---

## 5. Uninstall Terraform

### **Windows**
- Delete the Terraform folder and remove the PATH entry.

### **macOS**
```bash
brew uninstall terraform
```

### **Linux**
```bash
sudo apt-get remove terraform
```

---

✅ **You have successfully installed Terraform!**



# Terraform – Declarative vs Imperative

## Question 1

**Q:** What is the difference between Declarative and Imperative approaches in infrastructure as code, particularly in Terraform?

**A:**

**Declarative Approach:** You define the desired end state of your infrastructure, and Terraform automatically figures out the actions needed to achieve that state. You only describe what you want, not how to get there.

**Imperative Approach:** You explicitly provide the step-by-step instructions for creating or modifying resources. You define both what to do and how to do it.

**Example:**

**Declarative (Terraform):**
```hcl
resource "aws_s3_bucket" "my_bucket" {
  bucket = "my-example-bucket"
  acl    = "private"
}
```

Here, you simply state: “I want a private S3 bucket named `my-example-bucket`.” Terraform plans and applies the necessary steps to achieve this state.

**Imperative (AWS CLI):**
```bash
aws s3 mb s3://my-example-bucket
aws s3api put-bucket-acl --bucket my-example-bucket --acl private
```

Here, you manually instruct AWS step-by-step to create the bucket and set permissions.

---

## Question 2

**Q:** Why does Terraform use a declarative approach instead of an imperative one?

**A:**

Terraform uses a declarative approach because:

- **State Management:** Terraform maintains a state file to track the current infrastructure, enabling it to detect and apply only the necessary changes.
- **Idempotency:** You can apply the same configuration multiple times, and Terraform ensures the end state remains consistent without recreating resources unnecessarily.
- **Scalability:** For large environments, you don’t need to manually code each step; Terraform computes the optimal sequence.
- **Reduced Human Error:** By focusing on what is needed rather than how to build it, there is less chance of skipping or duplicating steps.

---

## Question 3

**Q:** Can Terraform perform imperative actions?

**A:**

Terraform is primarily declarative, but it can perform imperative-like tasks using:

- `terraform taint` to manually mark a resource for recreation.
- **Provisioners** (like `local-exec` or `remote-exec`) to run specific commands.
- Manual CLI commands for certain urgent changes, although this is not best practice since it bypasses Terraform’s state management.

---

## Question 4

**Q:** Can you give a real-life analogy for Declarative vs Imperative in Terraform?

**A:**

- **Declarative:** Telling an interior designer, “I want my living room to look modern with blue walls and a grey sofa.” They decide how to paint, arrange furniture, and buy decor.
- **Imperative:** Telling the designer, “First, buy 5 litres of blue paint, then paint the walls from top to bottom, then place the sofa in the corner at a 45-degree angle.”

---

## Question 5

**Q:** What are the key benefits of declarative infrastructure as code?

**A:**

- Predictable and consistent deployments.
- Easy to understand and maintain.
- Terraform can automatically detect and correct configuration drift.
- Can be version-controlled like regular code.

