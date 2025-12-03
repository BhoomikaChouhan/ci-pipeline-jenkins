# Jenkins CI Pipeline on AWS for Java Application

![Build Status](https://img.shields.io/badge/Build-Passing-brightgreen)
![AWS](https://img.shields.io/badge/Cloud-AWS%20EC2-orange)
![Jenkins](https://img.shields.io/badge/CI-Jenkins-red)
![SonarQube](https://img.shields.io/badge/Quality-SonarQube-blueviolet)
![Nexus](https://img.shields.io/badge/Artifacts-Nexus-yellow)

## 📖 About the Project

This repository hosts the **Continuous Integration (CI) pipeline** configuration for a Java-based application. 

**Note:** As a DevOps Engineer, my primary focus in this project is setting up the **CI automation, AWS Infrastructure, and Code Quality Analysis**. The Java application source code serves as a sample to demonstrate the capabilities of this pipeline.

## 🏗️ Architecture & Infrastructure

The entire infrastructure for this pipeline is hosted on the **AWS Cloud** using **EC2 instances**.

Architecture Diagram

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/f4e487c7-907f-4df2-a8a9-1c0caf4be6bd" />

### Infrastructure Setup:
* **Jenkins Server:** Hosted on a dedicated AWS EC2 instance (Master node).
* **SonarQube Server:** Hosted on a separate EC2 instance with PostgreSQL database.
* **Nexus Repository:** Running on a standalone EC2 instance for artifact management.
* **Security Groups:** Configured to allow traffic between Jenkins, SonarQube, and Nexus on specific ports (8080, 9000, 8081).

## 🚀 Key Features

The pipeline is designed to automate the build and quality assurance process using the following tools:

* **Cloud Platform:** AWS (EC2 instances for hosting servers).
* **Version Control:** GitHub with Webhook integration.
* **Build Tool:** Maven (Clean, Compile, Test, Package).
* **Code Quality:** Maven Checkstyle & SonarQube (Static Analysis).
* **Quality Gates:** Automated build failure if code quality does not meet standards.
* **Artifact Management:** Storing successful builds in Sonatype Nexus.

## 🛠️ Tools & Technologies

| Category | Tool |
| :--- | :--- |
| **Cloud Provider** | AWS (EC2) |
| **Orchestrator** | Jenkins |
| **Build Tool** | Maven |
| **Code Analysis** | SonarQube, Checkstyle |
| **Artifact Repo** | Sonatype Nexus |
| **SCM** | GitHub |
| **OS** | Linux (Ubuntu/Amazon Linux) |

## ⚙️ Pipeline Workflow

The `Jenkinsfile` orchestrates the following automated workflow:

1.  **Git Checkout:** Triggered via GitHub Webhook on commit.
2.  **Build & Unit Test:** Executes `mvn clean install`.
3.  **Static Code Analysis:** Runs Checkstyle to verify coding standards.
4.  **SonarQube Scan:** Pushes code analysis reports to the SonarQube server running on EC2.
5.  **Quality Gate Check:**
    * Jenkins pauses to check the Quality Gate status from SonarQube.
    * **Pass:** Proceed to the next stage.
    * **Fail:** The pipeline is aborted immediately.
6.  **Publish Artifact:** Uploads the generated `.jar` file to the Nexus Repository Manager on EC2.

## 📋 Prerequisites

To replicate this setup, you need:

1.  **AWS Account:** To launch EC2 instances.
2.  **Jenkins Server:** Installed on EC2 (Port 8080).
3.  **SonarQube Server:** Installed on EC2 (Port 9000).
4.  **Nexus Server:** Installed on EC2 (Port 8081).
5.  **Connectivity:** Ensure Security Groups allow traffic between these instances.
6.  **Webhooks:** Public IP of Jenkins configured in GitHub Webhooks.

## 📝 Usage

1.  Clone this repository.
2.  Set up the necessary servers on AWS EC2.
3.  Configure global tool configuration in Jenkins (Maven, JDK, SonarScanner).
4.  Create a new Pipeline job in Jenkins.
5.  Link this Git repository.
6.  Trigger the build manually or push a commit to test the Webhook.

# Technologies Versions Used
####
- JDK 17 or 21
- Maven 3.9
- MySQL 8

# Multitier Java App Tech Stack 
- Spring MVC
- Spring Security
- Spring Data JPA
- Maven
- JSP
- Tomcat
- MySQL
- Memcached
- Rabbitmq
  

---
*Created by [Bhoomika Chouhan](https://github.com/BhoomikaChouhan)*




