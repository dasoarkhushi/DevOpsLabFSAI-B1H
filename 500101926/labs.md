# *Lab 1: Basic Linux, Git, and CI/CD Commands*

---

## *Installing WSL and NixOS*

### *1. Install Ubuntu using WSL*

To install *Ubuntu* using *Windows Subsystem for Linux (WSL), run the following command in **PowerShell*:

sh
wsl --install -d Ubuntu


---

### *2. Install NixOS in Single-User Mode*

For a *NixOS single-user installation*, follow the official documentation for proper setup.

---

## *Using Git Bash*

*Git Bash* provides a *Linux-like terminal experience* on *Windows, enabling the use of **standard Linux commands*.

### *Common Linux Commands in Git Bash*

- ls → Lists files and directories.
- pwd → Prints the current working directory.
- cd Desktop → Changes the directory to the *Desktop*.

---

## *Basic Git Commands*

### *1. Cloning a Repository*

To *clone* a Git repository, use:

sh
git clone "https://github.com/yourrepository.git"


---

### *2. Checking Remote Repositories*

sh
git remote -v


---

### *3. Viewing Branches*

sh
git branch


---

### *4. Checking Commit History*

sh
git log


---

### *5. Checking Repository Status*

sh
git status


---

### *6. Viewing Differences Between Commits*

sh
git diff


---

### *7. Adding and Committing Changes*

sh
git add filename
git commit -m "Your commit message"


---

### *8. Configuring Git with Your Name*

sh
git config --global user.name "Khushidasoar"


---

## *Creating Files and Directories*

To *create files* for different purposes:

sh
touch home
touch office


These commands create *empty files* named *home* and *office* in the *current directory*.

---

# *CI/CD Basics*

---

## *What is CI/CD?*

- *CI (Continuous Integration):* Automatically *builds and tests code* whenever changes are pushed to a repository.
- *CD (Continuous Delivery/Deployment):* Automatically *delivers code* to *production* or *staging environments* after passing tests.

---

## *Common CI/CD Tools:*

- *GitHub Actions:* Native to *GitHub, ideal for **automation workflows*.
- *Jenkins:* *Open-source* automation server with a strong *plugin ecosystem*.
- *GitLab CI/CD:* Integrated within *GitLab* for *pipelines*.
- *CircleCI:* Specializes in *continuous integration and deployment*.
- *Travis CI:* Known for *simplicity* and *integration with GitHub*.

---

## *Basic CI/CD Pipeline Steps:*

1. *Build:* Compile the code and dependencies.
2. *Test:* Run automated tests to ensure code quality.
3. *Deploy:* Push the application to a *production* or *staging environment*.
4. *Monitor:* Ensure the application is running smoothly and handle *errors* if they occur.

---

## *Example: Setting Up a Simple GitHub Action*

Create a **.github/workflows/ci.yml** file:

yaml
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


---
# *Lab 2: Installing WSL (Windows Subsystem for Linux) on Windows*

The Windows Subsystem for Linux (WSL) provides a robust and efficient way to run a Linux environment directly on Windows without the overhead of a virtual machine. This guide outlines a professional and streamlined approach to installing WSL on your Windows system.

---

## *Step 1: Enable WSL*

1. *Open PowerShell as Administrator:*
   - Right-click on the *Start* button and select *Windows Terminal (Admin)* or *PowerShell (Admin)*.

2. *Install WSL:*
   - Run the following command to enable WSL and install the default Linux distribution (typically Ubuntu):
   sh
   wsl --install
   

3. *Restart Your Computer:*
   - A system reboot may be required to complete the installation process.

---

## *Step 2: Verify the WSL Installation*

To verify which version of WSL is installed, execute the following command:
sh
wsl --list --verbose


If WSL 2 is not installed, update it using:
sh
wsl --update


---

## *Step 3: Install a Linux Distribution*

1. *List Available Distributions:*
   sh
   wsl --list --online
   

2. *Install Your Preferred Distribution:*
   For example, to install *Ubuntu*, execute:
   sh
   wsl --install -d Ubuntu
   

3. *Set Up the Linux Environment:*
   Launch *Ubuntu* (or your chosen distribution) from the Start menu and follow the setup prompts to create a username and password.

---

## *Step 4: Configure WSL Version to WSL 2*

Set WSL 2 as the default version by running:
sh
wsl --set-default-version 2


To apply WSL 2 to a specific distribution:
sh
wsl --set-version Ubuntu 2


---

## *Step 5: Update the WSL Kernel (Optional)*

If prompted to update WSL 2, download and install the latest kernel update from Microsoft:
[Download WSL Kernel Update](https://aka.ms/wsl2kernel)

---

## *Step 6: Execute Linux Commands in WSL*

You can now run Linux commands through:
- The *WSL terminal* (e.g., Ubuntu or other distributions)
- *Windows Terminal*
- *PowerShell* or *Command Prompt*, using the wsl prefix:
sh
wsl ls -la


---

## *Step 7: Access Windows Files from WSL*

Access your Windows files from the WSL terminal using the /mnt/c/ directory:
sh
cd /mnt/c/Users/jaanh
ls


---

## *Step 8: Uninstalling WSL (Optional)*

To completely remove WSL from your system, follow these steps:

1. *Remove Linux Distributions:*
   - Navigate to *Settings > Apps* and uninstall the Linux distributions.

2. *Unregister WSL Distributions:*
   sh
   wsl --unregister <DistroName>
   

3. *Disable WSL Feature:*
   sh
   dism.exe /online /disable-feature /featurename:Microsoft-Windows-Subsystem-Linux /norestart
   

4. *Restart Your System* to finalize the changes.

---
# *Lab 3: Git Basics*

## *Using SSH and HTTP for Git*

### *SSH Key Setup*

Using SSH ensures secure access to Git repositories by utilizing both public and private keys.

---

### *1. Generating an SSH Key*
Generate an SSH key by running the following command:
sh
ssh-keygen -t ed25519 -C "dasoark@gmail.com"


Verify the key is generated at the default location:
sh
ls ~/.ssh


---

### *2. Viewing the SSH Key*
To read the SSH key, use the following command:
sh
cat ~/.ssh/id_ed25519.pub


---

### *3. Adding the SSH Key to the SSH-Agent*
sh
ssh-add ~/.ssh/id_ed25519


---

### *4. Adding the Key to GitHub*
- Navigate to *GitHub Settings → SSH and GPG keys → Add a new key*.
- Copy and paste the contents of id_ed25519.pub.

---

### *Cloning a Repository Using SSH*
sh
git clone git@github.com:dasoarkhushi/DemoMain.git


---

### *Cloning a Repository Using HTTP*
sh
git clone https://github.com/dasoarkhushi/DemoMain.git


When using HTTP, Git will prompt for your credentials if authentication is required.

---

## *Git Workflow*

### *1. Initialize and Clone a Repository*
sh
git init
git clone <repository-url>


---

### *2. Working on a Repository*
1. Navigate to the repository directory.
2. Make necessary changes.
3. Add changes to the staging area:
sh
git add .

4. Commit changes with a descriptive message:
sh
git commit -m "Your commit message"


---

### *3. Resolving Merge Conflicts*
To avoid merge conflicts, always pull the latest changes before pushing:
sh
git pull origin main
git merge


Push the changes to the repository:
sh
git push origin main


---

## *VIM Commands (for Git commit messages)*

sh
1. i → Insert mode
2. q → Quit
3. esc → Changing modes
4. shift + v → Visual mode
   - y → Copy / shift + insert
   - p → Paste
5. ‘H’, ‘J’, ‘K’, ‘L’ → Move left, up, down, right
6. dd → Delete the line
7. u → Undo
8. /something → Search something
9. esc + :wq → Save and quit


---
# *Lab 4: GIT Branching / Merge / Rebase*

## 1. *Creating Directories and Files:*

- **mkdir project**: Creates a project directory.
- **cd project**: Navigates into the project directory.
- **mkdir src**: Creates a src directory inside the project directory.
- **touch README.md**: Creates a README.md file.
- **touch z.txt**: Creates a z.txt file in featureA branch.
- **touch x.txt**: Creates a x.txt file in featureA branch.
- **touch s.txt**: Creates a s.txt file in main branch.

## 2. *Working with Files:*

- **echo "Hello World" >> README.md**: Adds "Hello World" to README.md.
- **echo "content" >> README.md && cat README.md**: Appends content to README.md and displays it:
  
  
  Hello World 1
  content
  
  
- **echo -e "hello \n me"**: Correctly prints the string with a newline:
  
  
  hello
  me
  
  
- **echo "Hello World 1" > README.md**: Rewrites README.md with "Hello World 1".

## 3. *Git Commands:*

- **git init**: Initializes a new Git repository.
- **git remote -v**: Displays remote repositories (none added here).
- **git status**: Shows the status of files in the repository.
- **git add .**: Stages all changes in the directory.
- **git commit -m "message"**: Commits staged changes with a message.
- **git log**: Displays commit history.

## 4. *Branching and Switching:*

- **git branch**: Lists branches in the repository.
- **git branch -M main**: Renames the current branch to main.
- **git checkout featureA**: Switches to the featureA branch.
- **git branch featureA**: Creates a featureA branch.
- **git checkout -b featureB**: Creates and switches to featureB.
- **git checkout main**: Switches to the main branch.

## 5. *Git Operations:*

- **git reset --soft <commit>**: Resets to a previous commit without changing the working directory.
- **git rebase main**: Rebases the featureA branch onto the main branch.
- **git merge featureB**: Merges the featureB branch into the main branch.
- **git reset --hard <commit>**: Resets the working directory and commit history to a specific commit.
- **git merge --squash featureB**: Squashes all the commits from featureB into a single commit without updating the HEAD.

## 6. *Final Content of Files:*

- **README.md**:
  
  Hello World 1
  content
  
  
- **z.txt** (created in featureA branch): Empty initially but added and committed.
- **x.txt** (created in featureA branch): Empty initially but added and committed.
- **b.txt**: Added in the main branch with commit message "Added b.txt".
- **s.txt**: Added in the main branch with commit message "s file added in main".
  

---

# *Lab 5: Git Submodules*

## *Git Workflow for Multiple Repositories and Submodules*

This session involves:

- Cloning multiple repositories
- Creating files
- Adding and committing changes
- Setting up Git submodules
- Pushing updates to remote repositories

---

## *Step 1: Cloning Repositories*

You cloned three repositories from GitHub:

sh
git clone https://github.com/khushidasoar/DemoMain.git
git clone https://github.com/khushidasoar/DemoCSS.git
git clone https://github.com/khushidasoar/DemoJS.git


💡 Note: There was an error (gir clone instead of git clone).

---

## *Step 2: Creating Files in Each Repository*

### In DemoJS repository:
sh
cd DemoJS
touch script.js


### In DemoCSS repository:
sh
cd ../DemoCSS
touch style.css


### In DemoMain repository:
sh
cd ../DemoMain
touch index.html


---

## *Step 3: Committing and Pushing Changes*

For each repository, you added, committed, and pushed the files.

### For DemoMain
Earliest to latest commits:
sh
git add .
# 1st commit
git commit -m "Added basic website HTML file"
# 2nd commit
git commit -m "this is a commit"
# 3rd commit
git commit -m "Path added"
# 4th commit
git commit -m "Merge branch 'main' of https://github.com/khushidasoar/DemoMain"
# 5th commit
git commit -m "made a change in index.html style.css"
# 6th commit
git commit -m "css folder deleted"
# 7th commit
git commit -m "Added CSS folder"
# 8th commit
git commit -m "sync"

git push


### For DemoJS
Earliest to latest commits:
sh
git add .
# 1st commit
git commit -m "Added script.js"
# 2nd commit
git commit -m "Js"
# 3rd commit
git commit -m "js configured"

git push


### For DemoCSS
Earliest to latest commits:
sh
git add .
# 1st commit
git commit -m "css file"
# 2nd commit
git commit -m "folder"
# 3rd commit
git commit -m "CSS"
# 4th commit
git commit -m "css changed backgroundcolor"

git push


---

## *Step 4: Setting Up Git Submodules*

You added DemoCSS and DemoJS as submodules inside DemoMain:

sh
git submodule add git@github.com:khushidasoar/DemoCSS.git css
git submodule add git@github.com:khushidasoar/DemoJS.git js


Then, you committed and pushed the changes:

sh
git commit -m "added css to main"
git push


sh
git commit -m "added js to main"
git push


---

## *Step 5: Verifying Repository Status*

Checking the status:

sh
git status

---

## *Explanation of the Workflow*

This document demonstrates a structured approach to managing multiple repositories with Git submodules. The key steps include:

1. *Cloning Repositories:* Downloading code from remote repositories to the local environment.
2. *File Creation:* Establishing required files (index.html, style.css, script.js) in respective repositories.
3. *Commit Management:* Accurate and sequential commit messages reflect project history transparently.
4. *Submodule Integration:* Adding external repositories (DemoCSS, DemoJS) as submodules in DemoMain for modular project management.
5. *Verification of Status:* Using git status to ensure the working directory is clean and ready for future development.


# *DevOps Lab 6*

## *Git FastAPI - Dockerization*

### *Install pipenv in WSL*

### *Install FastAPI and Uvicorn*

### *Write a FastAPI application with two GET endpoints:*

One returning a fixed JSON response with name and location.
Another that takes a path parameter and returns it in the response.

python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"Name": "Jaanhvi", "Location": "Lucknow"}

@app.get("/{data}")
def read_data(data: str):
    return {"hi": data, "Location": "Lucknow"}


Run this command to host the application:

sh
uvicorn main:app


Add this code to the Python file:

python
if __name__ == "__main__":
    uvicorn.run("main:app", host="0.0.0.0", reload=True, port=80)


Run the command:

sh
python main.py


### *Create a Dockerfile:*

Dockerfile
FROM ubuntu

RUN apt update -y
RUN apt install python3 python3-pip pipenv -y

WORKDIR /app
COPY . /app/
RUN pipenv install -r requirements.txt

EXPOSE 80
CMD pipenv run python3 ./main.py


### *Create a requirements.txt file:*


uvicorn
fastapi


### *Use the build command to create a Docker image:*

sh
docker build -t test02 .


### *Use the run command to execute the Docker image:*

sh
docker run -p 80:80 test02:latest



# Lab 7: GIT Fork and Open-Source

## Steps:

### 1. Open the desired repository to fork
- Navigate to the repository on GitHub.

### 2. Click on Fork
- Click the *Fork* button in the top-right corner.

### 3. Add a description and create your forked repository
- Provide an optional description.
- Click *Create Fork*.

### 4. Clone the repository locally
sh
git clone "git@github.com:khushidasoar/DevOpsLabFSAI-B1H.git"


### 5. Create a folder with your SAP ID
sh
mkdir 500101926
cd "./500101926"


### 6. Create a README.md file
sh
touch README.md


### 7. Edit the README.md file
sh
nano README.md


### 8. Commit the change
sh
git add .
git commit -m "Add README.md for khushi Dasoar (500101926)"
git push


### 9. Generate a pull request
- Navigate to your forked repository on GitHub.
- Click *Compare & pull request*.
- Provide a meaningful description of your changes.
- Click *Create pull request*.

Pull request generated, now moderators can review and accept the changes.**

---



# DevOps Lab 8 – Build using Jenkins

*Name:* khushi dasoar 
*SAP ID:* 500101926
*Roll Number:* R2142220097  
*Program:* B.Tech CSE (Full Stack AI) – Honours  
*College:* UPES Dehradun  
*Lab Title:* Jenkins-based CI/CD for Dockerized FastAPI Application  
*Repository:* [https://github.com/jaanhvisaxena/fastapi-dockerize-jenkins-lab]

---

## Objective

To automate the CI/CD process using Jenkins for a Python FastAPI application by building a Docker image and pushing it to Docker Hub upon each code push or manual trigger.

---

## Tools & Technologies Used

- Jenkins (Self-hosted CI/CD server)
- Docker (Container platform)
- Docker Hub (Image registry)
- FastAPI (Python web framework)
- Git (Version control)

---

## FastAPI App Code (main.py)

python
from fastapi import FastAPI
import uvicorn

app = FastAPI()

@app.get("/")
def root():
    return {"name": "Jaanhvi", "Location": "Dehradun"}

@app.get("/{data}")
def dynamic(data: str):
    return {"hi": data, "Location": "Dehradun"}

if __name__ == "__main__":
    uvicorn.run("main:app", host="0.0.0.0", port=80, reload=True)


---

## Dockerfile

dockerfile
FROM ubuntu

RUN apt update -y && apt install -y python3 python3-pip pipenv

WORKDIR /app
COPY . /app/
RUN pipenv install -r requirements.txt

EXPOSE 80
CMD pipenv run python3 ./main.py


---

## Jenkins Configuration Steps

### 1. Create a Pipeline Job

- Go to Jenkins Dashboard → New Item → Select *Pipeline* → Name: FastAPI Docker Pipeline

### 2. Configure DockerHub Credentials

- Go to Jenkins → *Manage Jenkins* → *Credentials*
- Add new credentials:
  - Type: Username with password
  - ID: dockerhub-creds
  - Username: Your Docker Hub username
  - Password: Docker Hub access token

### 3. Jenkinsfile (Pipeline Script)

groovy
pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-creds')
    }

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Docker Login') {
            steps {
                sh "echo ${DOCKERHUB_CREDENTIALS_PSW} | docker login -u ${DOCKERHUB_CREDENTIALS_USR} --password-stdin"
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t yourdockerhubusername/fast_api_dockerize .'
            }
        }

        stage('Push Docker Image') {
            steps {
                sh 'docker push yourdockerhubusername/fast_api_dockerize'
            }
        }
    }
}


---

## Output / Result

- Jenkins checks out the source code from GitHub.
- Logs into Docker Hub using saved credentials.
- Builds the Docker image.
- Pushes the image to Docker Hub.

---

## Conclusion

This lab demonstrates how Jenkins can be used to set up a CI/CD pipeline for Dockerized applications. By using Jenkins with Docker, we automate the build and deployment workflow of a FastAPI application in a reproducible manner.
