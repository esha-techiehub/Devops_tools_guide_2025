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

✅ This document is written for beginners with **simple examples** so you can remember IAM concepts easily.
