# Jenkins CI/CD Pipeline with Docker (AWS EC2 + Docker Compose)

# 📌 Project Overview

This project demonstrates an end-to-end CI/CD pipeline using Jenkins and Docker. It automates the process of building, testing, and deploying applications in a containerized environment.
It includes:

* ReactJS Frontend
* Spring Boot Backend
* Observability stack (Jaeger + Prometheus)

---

# 🛠️ Technologies Used

| Layer             | Technology                                |
| ----------------- | ----------------------------------------- |
| Infrastructure    | Terraform, AWS EC2 (Amazon Linux)         |
| Container Runtime | Docker                                    |
| Orchestration     | Docker Compose                            |
| Frontend          | ReactJS                                   |
| Backend           | Spring Boot (Java 17)                     |
| Observability     | Jaeger (Tracing), Prometheus (Monitoring) |
| Version Control   | GitHub                                    |

---
# ⚙️ Features
* Automated build process using Jenkins
* Continuous Integration with GitHub
* Docker-based containerized deployment
* Pipeline as Code using Jenkinsfile
* Easy and scalable deployment process
```

# 📂 Project Structure

Jenkins_CICD_with_Docker/
│── Jenkinsfile
│── Dockerfile
│── application/
│── README.md

```
# 🔄 CI/CD Workflow 
* Developer pushes code to GitHub repository
* Jenkins detects changes using webhook/polling
* Jenkins pipeline triggers automatically
* Application is built and tested
* Docker image is created
* Container is deployed
```
# Architecture Diagram


                     ┌────────────────────────────┐
                     │        User Browser        │
                     │ http://<EC2-IP>:3000      │
                     └────────────┬───────────────┘
                                  │
                                  ▼
                  ┌────────────────────────────────┐
                  │       AWS EC2 Instance         │
                  │       (Amazon Linux)           │
                  └────────────┬───────────────────┘
                               │
                         Docker Engine
                               │
                    ┌──────────┴──────────┐
                    │   Docker Compose    │
                    └──────────┬──────────┘
                               │
        ┌──────────────┬──────────────┬──────────────┬──────────────┐
        ▼              ▼              ▼              ▼
┌────────────┐  ┌──────────────┐  ┌────────────┐  ┌──────────────┐
│ React App  │  │ Spring Boot  │  │ Jaeger UI  │  │ Prometheus   │
│ Port:3000  │  │ Port:7093    │  │ Port:16686 │  │ Port:9090    │
└────────────┘  └──────────────┘  └────────────┘  └──────────────┘

---

# What This Setup Does

Terraform automatically:

* Launches EC2 instance
* Installs Git & Docker
* Configures Docker Compose
* Clones application repository
* Updates frontend API URL dynamically
* Starts full stack using Docker Compose

---

# ▶️ How to Run

## Step 1: git Clone
https://github.com/Shruti7385/Jenkins_CICD_with_Docker.git
## Step 2: terraform init
## Step 3: Apply Configuration
terraform apply --auto-approve

```
---

# Terraform Outputs

```hcl
output "EC2-Instance-access-details" {
	value = "ssh -i C:/Users/Sushant/.ssh/id_ed25519 ec2-user@${aws_instance.servers.public_ip} \n"
}

output "SpringBoot-Application-Backend" {
	value = "http://${aws_instance.servers.public_ip}:7093 \n"
}

output "React-Application-Frontend" {
	value = "http://${aws_instance.servers.public_ip}:3000 \n"
}

output "Jaeger-Distributed-Tracing" {
	value = "http://${aws_instance.servers.public_ip}:16686 \n"
}

output "Prometheus-Monitoring" {
	value = "http://${aws_instance.servers.public_ip}:9090 \n"
}
```

---

# Application Access URLs

| Service               | URL                   |
| --------------------- | --------------------- |
| Frontend (ReactJS)    | http://<EC2-IP>:3000  |
| Backend (Spring Boot) | http://<EC2-IP>:7093  |
| Jaeger UI             | http://<EC2-IP>:16686 |
| Prometheus            | http://<EC2-IP>:9090  |

---

# SSH Access

```bash
ssh -i C:/Users/Sushant/.ssh/id_ed25519 ec2-user@<EC2_PUBLIC_IP>
```

---

# Key Features

* Fully automated infrastructure + application deployment
* Dynamic IP substitution in frontend
* Integrated observability (Tracing + Metrics)
* Single-command deployment using Terraform
* No manual Docker setup required

---

# 👩‍💻 Author 
Shrutika Vhanwade

---

