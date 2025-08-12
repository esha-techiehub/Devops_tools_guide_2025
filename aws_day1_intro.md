# AWS IAM (Identity and Access Management) – Layman Guide

## 1. What is IAM?
**Simple Meaning:** IAM is like the security guard of your AWS account. It controls **who** can enter (users), and **what** they can do (permissions).

**Example:** Imagine a company office. IAM is like the reception desk – it checks ID cards (login credentials) and decides if you can go to the conference room, server room, or just the cafeteria.

---

## 2. How to Create an IAM User?
**Simple Steps:**
1. Go to AWS Management Console → Search for **IAM**.
2. Click **Users** → **Add User**.
3. Enter username → Select **Programmatic access** or **Console access**.
4. Attach permissions (like `AdministratorAccess` or custom).
5. Review & create the user.

**Example:** Just like making an employee ID card with specific building access.

---

## 3. What is Federation?
**Simple Meaning:** Federation lets people log in to AWS using an **existing account** (like Google, Microsoft, or corporate login) instead of making a new IAM user.

**Example:** Like entering a mall using your **driver’s license** instead of making a special “mall ID card”.

---

## 4. What are Policies?
**Simple Meaning:** Policies are permission documents in AWS that decide what a user **can** or **cannot** do.

**Example:** Like office rules: “You can enter meeting rooms, but not the server room.”

---

## 5. Are Policies Equal to Actions?
No.  
- **Policy**: The document that lists allowed or denied actions.  
- **Action**: The specific thing you can do (e.g., `s3:ListBucket`).

**Example:**  
Policy = “Ravi can drive cars and bikes.”  
Action = “Driving a car” or “Driving a bike”.

---

## 6. How to Create a Custom Policy?
**Steps:**
1. Open IAM → **Policies** → **Create Policy**.
2. Choose **JSON editor** or **Visual editor**.
3. Add the actions, resources, and conditions you want.
4. Save the policy and attach it to a user/group/role.

**Example:** Making your own rulebook for your house – “Friends can enter kitchen but not bedroom.”

---

## 7. Difference Between Permission Policies and Boundary Policies

| **Permission Policy** | **Boundary Policy** |
|-----------------------|--------------------|
| Main rules that give access. | A limit that says "Even if you have permissions, you cannot go beyond this boundary." |
| Directly attached to user/role. | Works like a fence for maximum allowed permissions. |
| Example: “You can access S3.” | Example: “Even if you have S3 access, you cannot delete objects.” |

**Example:**  
Permission policy = “You can drive a car.”  
Boundary policy = “You can drive only inside the city, not outside.”

---

## 8. How to Create an Alias Name for the AWS Account ID & Uses
**Steps:**
1. Go to IAM dashboard.
2. In **Account settings**, find **Account alias**.
3. Add a custom name (e.g., `mycompany-prod` instead of `123456789012`).

**Uses:** Easier to remember and share login URL.  
Example: Instead of telling employees “Log in at https://123456789012.signin.aws.amazon.com/console”, you can say “Log in at https://mycompany-prod.signin.aws.amazon.com/console”.

---

## 9. What is Authentication, Authorization, and Accountability?

### **Authentication**  
- **Meaning:** Proving you are who you say you are.  
- **Example:** Showing your ID card to security.  
- **AWS Example:** Logging in with username & password.

### **Authorization**  
- **Meaning:** Deciding what you are allowed to do.  
- **Example:** Having a pass to enter only certain floors.  
- **AWS Example:** IAM policy lets you access S3 but not EC2.

### **Accountability**  
- **Meaning:** Tracking who did what.  
- **Example:** CCTV cameras recording who entered which room.  
- **AWS Example:** CloudTrail logs recording all actions.

---
## 1. What is AWS CloudTrail?
**Simple Meaning:**  
CloudTrail is like a **CCTV camera** for your AWS account. It records everything that happens – who did what, when, and from where.

**Example:**  
In an office, CCTV records when an employee entered, which room they went to, and what they did. CloudTrail does the same but for AWS actions.

---

## 2. Why is it Used?
- To **track all user activities** for security and compliance.
- To **investigate problems** by checking what happened before an issue.
- To **audit** (prove) what actions were taken in AWS.
- To **detect unusual activity** and possible security breaches.

**Example:**  
If someone deleted an important file in AWS S3, CloudTrail can show *who* did it, *when*, and *how*.

---

## 3. How to Track All User Activities?
1. **Enable CloudTrail** (usually on by default for event history).
2. Go to **AWS Console → CloudTrail**.
3. Use **Event History** to search by:
   - User name
   - Time
   - Resource type
   - Event name (like `CreateBucket` or `TerminateInstances`)
4. You can **create a Trail** to store logs in S3 for long-term history.

**Example:**  
Like reviewing CCTV footage by date, person, or activity.

---

## 4. Key CloudTrail Terminologies

### **Event History**
- Shows the last 90 days of AWS API calls and activities for free.
- Good for quick lookups.

**Example:**  
Like CCTV’s “recent 3-month footage” that you can check instantly.

---

### **Trail**
- A setup that **continuously records events** and stores them in an S3 bucket for as long as you want.
- Can be single-region or multi-region.

**Example:**  
Like saving CCTV footage in a storage room for years.

---

### **Management Events**
- Track control actions like creating/deleting resources.
- Example: `CreateUser`, `DeleteBucket`.

**Example:**  
Like logging “who got new office keys” or “who closed a meeting room”.

---

### **Data Events**
- Track actions **on the actual data** inside services.
- Example: `GetObject` in S3 (downloading a file), `PutObject` (uploading a file).

**Example:**  
Like noting every time someone reads or writes a document in a filing cabinet.

---

### **Insights Events**
- Detect unusual patterns or activities.
- Example: Suddenly having 200 `TerminateInstance` calls in 1 hour.

**Example:**  
Like security noticing an employee coming in and out 50 times in a day.

---

## 5. Summary
CloudTrail = AWS's CCTV + activity log system.  
It helps in **security, auditing, and problem-solving** by tracking every action in your account.

## 3. Ways to Access AWS

AWS can be accessed in multiple ways, just like using a bank in different methods.

---

### 1. AWS Management Console
- **Meaning:** Web interface for managing AWS.
- **Example:** Banking website.
- **Steps:**
  1. Go to `https://aws.amazon.com/console/`
  2. Login with credentials.
  3. Manage services visually.

---

### 2. AWS CLI (Command Line Interface)
- **Meaning:** Run commands in terminal to manage AWS.
- **Example:** Speaking commands to bank clerk.
- **Steps:**
  1. Install AWS CLI.
  2. Run `aws configure` to set credentials.
  3. Use commands like `aws s3 ls`.

---

### 3. AWS SDKs
- **Meaning:** Libraries to connect AWS with your code.
- **Example:** Mobile banking API.
- **Steps:**
  1. Choose language (Python, Java, etc.).
  2. Install SDK (`pip install boto3`).
  3. Write code to call AWS services.

---

### 4. AWS Mobile App
- **Meaning:** Manage AWS from your phone.
- **Example:** Banking mobile app.
- **Steps:**
  1. Install AWS Console app.
  2. Login with AWS credentials.

---

### 5. AWS CloudShell
- **Meaning:** Browser-based terminal in AWS Console.
- **Example:** Service desk inside the bank.
- **Steps:**
  1. Login to AWS Console.
  2. Open CloudShell icon.
  3. Run CLI commands.

---

### 6. AWS API
- **Meaning:** Directly send requests to AWS over the internet.
- **Example:** Sending a secure instruction letter to the bank.
- **Steps:**
  1. Identify API endpoint.
  2. Authenticate request.
  3. Send HTTP requests.

---

### Quick Summary Table

| Method                | Best For                                  | Example Analogy                  |
|-----------------------|-------------------------------------------|-----------------------------------|
| AWS Management Console | Beginners & quick changes                 | Web banking site                  |
| AWS CLI               | Developers, automation scripts            | Speaking commands to bank clerk   |
| AWS SDKs              | Application integration                   | Mobile banking API                |
| AWS Mobile App        | Monitoring AWS on the go                   | Banking mobile app                |
| AWS CloudShell        | Running commands without local setup       | Service desk inside bank          |
| AWS API               | Advanced integrations & automation        | Secure instruction letter to bank |

---


