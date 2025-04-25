# **Lab 1: Basic Linux, Git, and CI/CD Commands**

---

## **Installing WSL and NixOS**

### **1. Install Ubuntu using WSL**

To install **Ubuntu** using **Windows Subsystem for Linux (WSL)**, run the following command in **PowerShell**:

```sh
wsl --install -d Ubuntu
```

---

### **2. Install NixOS in Single-User Mode**

For a **NixOS single-user installation**, follow the official documentation for proper setup.

---

## **Using Git Bash**

**Git Bash** provides a **Linux-like terminal experience** on **Windows**, enabling the use of **standard Linux commands**.

### **Common Linux Commands in Git Bash**

- `ls` → Lists files and directories.
- `pwd` → Prints the current working directory.
- `cd Desktop` → Changes the directory to the **Desktop**.

---

## **Basic Git Commands**

### **1. Cloning a Repository**

To **clone** a Git repository, use:

```sh
git clone "https://github.com/yourrepository.git"
```

---

### **2. Checking Remote Repositories**

```sh
git remote -v
```

---

### **3. Viewing Branches**

```sh
git branch
```

---

### **4. Checking Commit History**

```sh
git log
```

---

### **5. Checking Repository Status**

```sh
git status
```

---

### **6. Viewing Differences Between Commits**

```sh
git diff
```

---

### **7. Adding and Committing Changes**

```sh
git add filename
git commit -m "Your commit message"
```

---

### **8. Configuring Git with Your Name**

```sh
git config --global user.name "Khushi Dasoar"
```

---

## **Creating Files and Directories**

To **create files** for different purposes:

```sh
touch home
touch office
```

These commands create **empty files** named **home** and **office** in the **current directory**.

---

# **CI/CD Basics**

---

## **What is CI/CD?**

- **CI (Continuous Integration):** Automatically **builds and tests code** whenever changes are pushed to a repository.
- **CD (Continuous Delivery/Deployment):** Automatically **delivers code** to **production** or **staging environments** after passing tests.

---

## **Common CI/CD Tools:**

- **GitHub Actions:** Native to **GitHub**, ideal for **automation workflows**.
- **Jenkins:** **Open-source** automation server with a strong **plugin ecosystem**.
- **GitLab CI/CD:** Integrated within **GitLab** for **pipelines**.
- **CircleCI:** Specializes in **continuous integration and deployment**.
- **Travis CI:** Known for **simplicity** and **integration with GitHub**.

---

## **Basic CI/CD Pipeline Steps:**

1. **Build:** Compile the code and dependencies.
2. **Test:** Run automated tests to ensure code quality.
3. **Deploy:** Push the application to a **production** or **staging environment**.
4. **Monitor:** Ensure the application is running smoothly and handle **errors** if they occur.

---

## **Example: Setting Up a Simple GitHub Action**

Create a **`.github/workflows/ci.yml`** file:

```yaml
name: CI Pipeline

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Set up Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '16'

    - name: Install dependencies
      run: npm install

    - name: Run tests
      run: npm test
```

---
