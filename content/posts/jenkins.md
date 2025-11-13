+++
date = '2025-07-08T12:15:56+05:00'
title = "Meet Jenkins: A Guide to Automation"
tags = ['jenkin', 'plugins', 'pipeline', 'shell','CI/CD']
+++

---

## What is Jenkins?

**Jenkins** is an open-source automation tool written in Java. It helps developers build, test, and deploy their software automatically, making **Continuous Integration (CI)** and **Continuous Delivery (CD)** possible.

```
CI: Continuous Integration
Automatically building and testing code whenever changes are pushed. 
CD: Continuous Delivery
 Automatically deploying/releasing the code to production or staging. 

Together, CI/CD makes your workflow faster, safer, and hands-free.
```

In simple terms:
> Jenkins watches your code and runs jobs (like building or testing) whenever you push changes — saving you tons of manual work.

Jenkins is a server.
It’s a program you install on a machine (your own computer, a VPS, or cloud) that:
   - • Runs 24/7.
   - • Waits for code changes (like GitHub push).
   - • Does tasks you define (build, test, deploy).
   - • Reports the results.

---

##  Why Use Jenkins?

- Automate repetitive tasks like testing and deploying.
- Supports a wide range of plugins and tools.
- Saves time in large teams and projects.
- Detects bugs early by testing code regularly.
- Web-based interface for managing jobs easily.

---

##  Key Concepts to Know

| Term | Meaning |
|------|---------|
| **Job / Project** | A task that Jenkins runs (e.g., build, test). |
| **Build** | The process of compiling code, running scripts, etc. |
| **Pipeline** | A set of steps that automate the process from build to deployment. |
| **Node / Agent** | A machine that runs Jenkins jobs (can be remote). |
| **Plugin** | Extension that adds new features to Jenkins. |

---

##  How to Install Jenkins on Ubuntu (Beginner-Friendly)

### Step 1: Install Java
![command screenshot](/jenkins/s1.png)

Then run:
![command screenshot](/jenkins/s2.png)

Check the Java version:
![command screenshot](/jenkins/s3.png)

### Step 2: Add Jenkins Repository
![command screenshot](/jenkins/s4.png)


### Step 3: Install Jenkins
![command screenshot](/jenkins/s7.png)

### Step 4: Start and Enable Jenkins
![command screenshot](/jenkins/s8.png)
![command screenshot](/jenkins/s9.png)

Then check the status if its active:
 ![command screenshot](/jenkins/s10.png)


### Step 5: Open Jenkins in Browser
Visit: http://localhost:8080

To unlock Jenkins, run:

![command screenshot](/jenkins/s13.png)

Paste the password in your browser when prompted.

Proceed with the steps required and
it will get you to the main Jenkins page:
![command screenshot](/jenkins/s18.png)


## Setting Up Your First Job (Freestyle Project)
1. Go to `Dashboard > New Item`

1. Choose `Freestyle project` and give it a name

3. In `Build Steps`, choose:

- `Execute shell` for Linux commands

- Or `Execute Windows batch command` for Windows

4. Add your script like:
```bash
echo "Hello from Jenkins!"
```
5. Click Save, then Build Now

Jenkins will run your job and show you output in the Console Output.

---

## Jenkins Pipeline (Scripted Automation)

Create a new **Pipeline** job and use the following example script:

```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying the project...'
            }
        }
    }
}
```

---

## Integrating Jenkins with Git (or GitLab)

Jenkins works best when connected to a version control system like **GitHub** or **GitLab**. This allows Jenkins to:

- Watch for new code pushes
- Automatically trigger builds and tests
- Pull code into your pipeline jobs

### Example (GitLab):

1. Install the **Git Plugin** (if not already).
2. Create a **Personal Access Token** in GitLab.
3. In Jenkins, go to `Credentials > Add Credentials` and enter your GitLab token.
4. Create a new Pipeline or Freestyle job.
5. Under `Source Code Management`, choose `Git` and paste your GitLab repo URL.

> Now every time you push to GitLab, Jenkins can respond automatically.
---

## Useful Plugins to Explore

| Plugin              | Purpose                                        |
|---------------------|------------------------------------------------|
| **Git Plugin**       | Integrate with Git repositories                |
| **GitHub Integration** | Trigger builds from GitHub pushes              |
| **Pipeline Plugin**  | Use `Jenkinsfile` for automation workflows     |
| **Email Extension**  | Send notifications based on build status       |
| **Docker Plugin**    | Build and run Docker containers via Jenkins    |
---

## Final Thoughts

Jenkins is like your project manager robot — it does the boring and repetitive tasks so you can focus on writing code.

With its powerful CI/CD pipelines, plugin ecosystem, and integration options, Jenkins is trusted by teams all over the world to ship better software — faster.

Once you're comfortable with the basics, explore more advanced topics like:

- Shared Libraries (DRY pipelines)
- Blue Ocean (visual pipeline editor)
- Dockerized builds
- Jenkins + Kubernetes or AWS for cloud deployments
- Jenkins + GitLab CI integration

 Jenkins is not just a tool, it’s the **engine behind modern DevOps**.

---

## Jenkins Installation Commands
```bash
sudo apt update
sudo apt install openjdk-17-jdk
java -version
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins-keyring.asc > /dev/null
echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo apt update
sudo apt install jenkins
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

