# Rapport

> A three-tier social media web application deployed on AWS with an automated continuous integration pipeline.

## Overview

**Rapport** is a three-tier social media web application designed to demonstrate the migration and modernization of a traditional application infrastructure using **Amazon Web Services (AWS)**.

The project follows a **Lift and Shift strategy** to host the application on AWS while introducing flexible, scalable cloud infrastructure and an automated continuous integration workflow.

It addresses common challenges associated with traditional infrastructure and manual software delivery, including complex infrastructure management, scalability limitations, high upfront capital expenditure, recurring operational costs, manual processes, difficult automation, and time-consuming deployments.

---

## Problem Statement

Traditional application environments often face:

* **Complex Management** — Managing servers and application infrastructure manually.
* **Scale Up/Down Complexity** — Difficulty dynamically adjusting infrastructure according to demand.
* **High Infrastructure Costs** — Upfront **CapEx** and recurring **OpEx** requirements.
* **Manual Processes** — Repetitive manual deployment and configuration tasks.
* **Difficult Automation** — Lack of automated development and deployment workflows.
* **Time Consumption** — Longer build, testing, and deployment cycles.

---

## Solution

Rapport leverages AWS cloud infrastructure and automation to provide:

* ☁️ **Cloud-Based Hosting** — Host and run the application on AWS for production.
* 🔄 **Lift and Shift Migration** — Migrate the existing application to AWS with minimal architectural changes.
* 📈 **Flexible Infrastructure** — Dynamically scale compute resources based on workload.
* 💰 **No Upfront Infrastructure Cost** — Utilize a pay-as-you-go cloud infrastructure model.
* ⚙️ **Automation** — Automate application build, testing, and infrastructure operations.
* 🚀 **Effective Modernization** — Establish a foundation for further cloud-native modernization.

---

## 🏗️ Three-Tier Architecture

Rapport follows a traditional three-tier application architecture:

```text
                    ┌──────────────────────┐
                    │       Users          │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Route 53 / DNS     │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Elastic Load       │
                    │     Balancer         │
                    └──────────┬───────────┘
                               │
                               ▼
              ┌────────────────────────────────┐
              │        Application Tier        │
              │                                │
              │   EC2 + Apache Tomcat + Java  │
              │   Auto Scaling                  │
              └───────────────┬────────────────┘
                              │
                 ┌────────────┼────────────┐
                 ▼            ▼            ▼
           ┌──────────┐ ┌──────────┐ ┌──────────┐
           │  MySQL   │ │ RabbitMQ │ │ Memcached│
           └──────────┘ └──────────┘ └──────────┘
                 │
                 ▼
           ┌──────────┐
           │   EBS    │
           └──────────┘
```

---

## 🛠️ Tech Stack

### 💻 Application

| Technology        | Purpose                                       |
| ----------------- | --------------------------------------------- |
| **Java**          | Application development                       |
| **Apache Tomcat** | Java application server                       |
| **Memcached**     | Application caching                           |
| **MySQL**         | Relational database                           |
| **RabbitMQ**      | Message broker for asynchronous communication |

### ☁️ AWS Infrastructure

| AWS Service                       | Purpose                                                   |
| --------------------------------- | --------------------------------------------------------- |
| **Amazon EC2**                    | Compute instances hosting Tomcat, RabbitMQ and Memcached  |
| **EC2 Auto Scaling**              | Automatically scales compute instances based on workload  |
| **Amazon S3**                     | Object storage for shared files and software artifacts    |
| **Amazon Route 53**               | DNS management and private hosted zones                   |
| **AWS Certificate Manager (ACM)** | HTTPS/TLS certificate management                          |
| **Elastic Load Balancing (ELB)**  | Distributes incoming application traffic across instances |
| **AWS IAM**                       | Identity and access management                            |
| **Amazon EBS**                    | Persistent block storage for EC2 instances                |

### 🔄 Continuous Integration

| Technology           | Purpose                                             |
| -------------------- | --------------------------------------------------- |
| **Bitbucket**        | Source code repository                              |
| **AWS CodeArtifact** | Maven dependency/package repository                 |
| **AWS CodeBuild**    | Automated application build and testing             |
| **SonarCloud**       | Automated source-code quality and security analysis |
| **Amazon SNS**       | Pipeline and build notifications                    |
| **AWS CodePipeline** | Orchestrates the continuous integration workflow    |

### ⚙️ Automation

| Technology  | Purpose                                                            |
| ----------- | ------------------------------------------------------------------ |
| **Ansible** | Configuration management and application/infrastructure automation |

---

## 🔄 Continuous Integration Workflow

```text
        ┌──────────────┐
        │   Bitbucket  │
        │ Source Code  │
        └───────┬──────┘
                │
                ▼
        ┌──────────────┐
        │ CodePipeline │
        └───────┬──────┘
                │
                ▼
        ┌──────────────┐
        │  CodeBuild   │
        │ Build & Test │
        └───────┬──────┘
                │
                ▼
        ┌──────────────┐
        │ CodeArtifact │
        │   Maven      │
        │ Dependencies │
        └───────┬──────┘
                │
                ▼
        ┌──────────────┐
        │  SonarCloud  │
        │ Code Quality │
        └───────┬──────┘
                │
                ▼
        ┌──────────────┐
        │     SNS      │
        │ Notifications│
        └──────────────┘
```

The pipeline connects the source repository, dependency management, automated builds, testing, code-quality analysis, and notifications into an automated development workflow.

---

## Key Features

### ☁️ AWS Cloud Deployment

The application is hosted on AWS infrastructure, providing flexible and scalable compute resources for production workloads.

### 🔄 Lift and Shift Strategy

The existing three-tier application can be migrated to AWS without requiring a complete redesign of the application architecture.

### 📈 Auto Scaling

EC2 Auto Scaling enables the infrastructure to dynamically adjust compute capacity according to application demand.

### ⚖️ Load Balancing

Elastic Load Balancing distributes incoming traffic across available application instances to improve availability and scalability.

### 🔐 Secure Infrastructure

AWS IAM, private DNS zones, HTTPS certificates, and controlled infrastructure access provide a foundation for secure cloud deployment.

### 🔁 Continuous Integration

CodePipeline automates the integration workflow by connecting source control, dependency management, application builds, testing, code analysis, and notifications.

### 🤖 Automation with Ansible

Ansible reduces repetitive manual configuration and deployment tasks through infrastructure and application automation.

---

## 📊 Benefits

* Reduced infrastructure management complexity
* Flexible scaling based on workload
* Automated build and testing process
* Faster development cycles
* Improved code quality monitoring
* Reduced manual intervention
* Cloud-based production infrastructure
* Pay-as-you-go cloud model
* Foundation for future modernization

---

## 🗺️ Future Improvements

* Containerize application using Docker
* Introduce Amazon ECS/EKS for container orchestration
* Migrate MySQL to Amazon RDS
* Replace self-managed RabbitMQ with Amazon MQ
* Introduce infrastructure as code using Terraform or AWS CloudFormation
* Implement a complete CI/CD deployment workflow
* Add centralized monitoring and logging
* Implement blue-green or rolling deployments

---

## 👥 Project

**Rapport** — Three-Tier Social Media Application with AWS Continuous Integration

Built to demonstrate **cloud migration, scalable infrastructure, automation, and continuous integration using AWS**.

---

## 📜 License

This project is intended for **educational and demonstration purposes**.

Unless explicitly stated otherwise, the source code and associated materials remain the intellectual property of the project author(s). Unauthorized reproduction, redistribution, modification, or commercial use is not permitted without prior permission.
