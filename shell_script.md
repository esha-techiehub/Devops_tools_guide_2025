
# 🐚 Shell Scripting for DevOps

[![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black)](https://www.kernel.org/)
[![Bash](https://img.shields.io/badge/Bash-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white)](https://www.gnu.org/software/bash/)
[![DevOps](https://img.shields.io/badge/DevOps-0052CC?style=for-the-badge&logo=azuredevops&logoColor=white)](https://azure.microsoft.com/en-us/overview/devops/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](https://opensource.org/licenses/MIT)

> Advanced guide for Linux, Shell scripting, and DevOps automation  

---

## **📌 Table of Contents**

<details>
<summary>Click to expand</summary>

1. [OS Fundamentals](#os-fundamentals)  
2. [Shell Scripting Fundamentals](#shell-scripting-fundamentals)  
3. [Bash / Shell Concepts](#bash--shell-concepts)  
4. [Linking Concepts](#linking-concepts)  
5. [Script Execution & Permissions](#script-execution--permissions)  
6. [DevOps Shell Scripting Use Cases](#devops-shell-scripting-use-cases)  
7. [Best Practices](#best-practices)  
8. [Quick Reference Commands](#quick-reference)  

</details>

---

## **OS Fundamentals**

**What is an OS?**  
An Operating System (OS) acts as an interface between hardware and software, managing CPU, memory, storage, and I/O devices.

<details>
<summary>Workflow of OS</summary>

1. Booting → load kernel into memory  
2. Process Management → schedule & manage processes  
3. Memory Management → allocate/deallocate memory  
4. File System Management → read/write files  
5. Device Management → interface with hardware  
6. Security & User Management → access control & permissions  

</details>

**Linux vs Windows**

| Feature | Linux | Windows |
|---------|-------|---------|
| Kernel | Monolithic | Hybrid |
| Open Source | ✅ Yes | ❌ No |
| Shell | Bash, Sh | PowerShell, CMD |
| Security | Strong (sudo + permissions) | Moderate (UAC) |
| File System | Ext4, XFS | NTFS, FAT32 |

**Linux OS Architecture**
```
User Space → System Libraries → Kernel → Hardware
```

**Core Components**  
- Kernel → Process, memory, device, file management  
- System Libraries → Pre-written code for apps  
- Compilers → Translate code to machine code  
- User Processes → Programs executed by users  
- System Software → Utilities supporting OS functionality  

**Kernel Responsibilities**  
- Process Management | Memory Management | Device Management  
- File System Handling | Security Enforcement  

**System Libraries Types**  
- Static (.a) → Linked at compile-time  
- Dynamic (.so / .dll) → Linked at runtime  

**System Software Examples**  
- Compilers (`gcc`)  
- Debuggers (`gdb`)  
- File Management Utilities  
- Assemblers  

---

## **Shell Scripting Fundamentals**

**What is Shell Scripting?**  
Automation using shell commands to simplify system administration and DevOps workflows.

<details>
<summary>File & Directory Operations</summary>

```bash
touch filename.sh      # create file
mkdir myfolder         # create folder
vi filename.sh         # edit using vi
nano filename.sh       # edit using nano
cat filename.sh        # read file
rm filename.sh         # delete file
rm -rf myfolder        # delete folder
```

</details>

**Popular Commands**
| Command | Description |
|---------|-------------|
| `pwd` | Print working directory |
| `ls` | List files & directories |
| `cd` | Change directory (`..`, `~`, `/`) |
| `ls -ltr` | List files with details |
| `df -h` | Disk usage (human readable) |
| `free -g` | Memory check (GB) |
| `nproc` | CPU cores |
| `top` | Real-time process & resource usage |
| `chmod` | Change permissions |
| `history` | Command history |

**Login to VM / Instance**
```bash
ssh -i <key_path.pem> ubuntu@<ip_address>
```

---

## **Bash / Shell Concepts**

**Shebang**
```bash
#!/bin/bash
```

**Shell Differences**
| Shell | Description |
|-------|-------------|
| `/bin/sh` | POSIX-compliant, simple |
| `/bin/bash` | Advanced Bash features |
| `/bin/dash` | Lightweight, fast, default in Ubuntu |

**Vim/Vi Basics**  
- `i` → Insert mode  
- `Esc` → Exit insert mode  
- `:wq!` → Save & exit (force)  
- `:q!` → Exit without saving  

---

## **Linking Concepts**

**Hard Link vs Soft Link**
```bash
ln originalfile hardlinkfile      # Hard Link
ln -s originalfile softlinkfile   # Soft Link (Symbolic)
```
- Hard Link → Points to inode, cannot cross filesystem  
- Soft Link → Points to file path, can cross filesystem  

---

## **Script Execution & Permissions**

```bash
chmod +x filename.sh   # Make executable
./filename.sh          # Run script
sh filename.sh         # Run with sh
```

**Permission Numbers**  
- Read = 4, Write = 2, Execute = 1  
- Example: `chmod 777 file` → full permissions  
```bash
chmod u+x,g-w,o-r file.sh   # Advanced permission
```

---

## **DevOps Shell Scripting Use Cases**

- Infrastructure automation  
- Code automation (Git)  
- Configuration management  

**Node Health Script Example**
```bash
#!/bin/bash
# Author: DevOps Team
# Date: 15-Oct-2025
# Version: v1.0
# Description: Check node health

echo "Disk Space:"
df -h

echo "Memory:"
free -g

echo "CPU cores:"
nproc

echo "Top processes:"
top -n 1
```

**Debugging Scripts**
```bash
set -x           # Debug mode
set -e           # Exit on error
set -o pipefail  # Detect errors in pipes
```

**Process Filtering Example**
```bash
ps -ef | grep amazon | awk '{print $2}'  # Print PID
```

**Handling stdout/stderr**
```bash
command > output.txt       # stdout
command 2> error.txt       # stderr
command &> all.txt         # both
```

---

## **Best Practices**

- Always add **metadata** to scripts:
```bash
# Author:
# Date:
# Version:
# Description:
```
- Use `man <command>` for detailed usage  
- Test scripts on **staging VM** first  
- Use `chmod` carefully in production  
- Debug scripts with `set -x`  

---

## **Quick Reference Commands**
```bash
pwd | cd | mkdir | ls -ltr | cat | rm -rf
chmod 777 filename.sh
./script.sh
set -x / set -e / set -o pipefail
ps -ef | grep process | awk '{print $2}'
```

---

## **Download Instructions**

1. Copy the content above and save it as `README.md`  
2. Or download it directly using a terminal:
```bash
curl -o README.md https://raw.githubusercontent.com/your-repo-link/README.md
```

---

> **✨ Notes:** This README is designed for DevOps engineers, Linux admins, and automation enthusiasts. Covers OS basics, Linux commands, shell scripting, permissions, debugging, and automation workflows.
