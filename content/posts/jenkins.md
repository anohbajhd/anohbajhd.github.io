+++
date = '2025-07-10T12:15:56+05:00'
title = "Meet Jenkins: A Guide to Automation"
tags = ['jenkin', 'plugins', 'pipeline', 'shell']
+++

---

## What is Jenkins?

**Jenkins** is an open-source automation tool written in Java. It helps developers build, test, and deploy their software automatically, making **Continuous Integration (CI)** and **Continuous Delivery (CD)** possible.

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
![command screenshot](/jenkins/s2.png)

### Step 2: Add Jenkins Repository
![command screenshot](/jenkins/s3.png)


### Step 3: Install Jenkins
![command screenshot](/jenkins/s4.png)

### Step 4: Start and Enable Jenkins
![command screenshot](/jenkins/s5.png)

### Step 5: Open Jenkins in Browser
Visit: http://localhost:8080
To unlock Jenkins, run:

![command screenshot](/jenkins/s6.png)

Paste the password in your browser when prompted.


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

## Useful Plugins to Explore

| Plugin              | Purpose                                        |
|---------------------|------------------------------------------------|
| **Git Plugin**       | Integrate with Git repositories                |
| **GitHub Integration** | Trigger builds from GitHub pushes              |
| **Pipeline Plugin**  | Use `Jenkinsfile` for automation workflows     |
| **Email Extension**  | Send notifications based on build status       |
| **Docker Plugin**    | Build and run Docker containers via Jenkins    |

## Final Thoughts
Jenkins is like your project manager robot — it does the boring and repetitive tasks so you can focus on writing code.

Once you're comfortable with the basics, you can explore advanced topics like:

- Shared libraries

- Blue Ocean UI

- Deploying with Docker, Kubernetes, or AWS