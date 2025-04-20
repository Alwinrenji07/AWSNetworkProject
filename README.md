# 🚀 Automated Container Deployment in AWS – B9IS121

This project is part of the **B9IS121 - Network Systems and Administration** module. It demonstrates how to automate infrastructure provisioning, server configuration, and containerized web app deployment using **Terraform**, **Ansible**, **Docker**, and **AWS**.

---

## 📁 Project Structure


---

## 🧰 Tools Used

| Tool         | Purpose                                        |
|--------------|------------------------------------------------|
| Terraform    | Infrastructure provisioning (EC2, VPC, etc.)   |
| Ansible      | EC2 configuration (install Docker, updates)    |
| Docker       | Containerize and run a sample web app (Nginx)  |
| Git & GitHub | Version control and code hosting               |

---

## ✅ Part 1: AWS Infrastructure Setup

- Created a custom **VPC** using Terraform
- Launched an **EC2 instance (Amazon Linux 2)** in a public subnet
- Configured a **Security Group** allowing:
  - SSH (port 22) from my IP
  - HTTP (port 80) from the world
- Connected instance to the internet via **Internet Gateway**

---

## ✅ Part 2: VPC and EC2 Configuration

- Set up:
  - Two **public** and two **private** subnets
  - **NAT Gateway** for private subnets
  - Proper route tables for internet access
- Used **Ansible** to configure EC2:
  - Installed Docker
  - Updated packages
  - Enabled Docker to run on boot

---

## ✅ Part 3: Docker Container Deployment

- Created a sample web page (`index.html`)
- Wrote a simple **Dockerfile** using `nginx:alpine`
- Used **Ansible** to:
  - Copy files to EC2
  - Build and run the container on port 80

---

## 🌐 Live Test

Visit the EC2 instance via:
http://56.228.3.160/


This loads the custom Nginx web page deployed in a Docker container.

---

## 🚀 How to Run the Project

### 1. Provision Infrastructure (Terraform)
```bash
cd terraform
terraform init
terraform apply
--------------------------------------------------------------------

Configure Server & Deploy App (Ansible)

cd ansible
ansible-playbook -i inventory.ini playbook.yml

---------------------------------------------------------------------
Architecture Diagram

                  [Internet]
                      |
              -------------------
              |    IGW (Public)  |
              -------------------
                      |
                [Route Table]
                      |
        -------------------------------
        |                             |
 [Public Subnet 1]          [Public Subnet 2]
        |                             |
     [EC2 Instance]                 [NAT Gateway]
                                        |
                        -------------------------------
                        |                             |
              [Private Subnet 1]           [Private Subnet 2]


-----------------------------------------------------------------------


Author

Alwin Renji
Module: B9IS121 – Network Systems and Administration
Instructors: Dr. Basel Magableh
