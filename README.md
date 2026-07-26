# Ansible Multi-Tier Infrastructure Automation

A production-inspired Infrastructure as Code (IaC) project that automates the provisioning and configuration of a complete multi-tier application architecture using **Ansible**.

This project demonstrates how Ansible can be used to automate server provisioning, application deployment, database configuration, cache setup, reverse proxy management, and secure secrets handling while following Infrastructure as Code best practices.

---

# Project Overview

Managing multiple servers manually is error-prone, time-consuming, and difficult to scale.

This project solves that problem by using **Ansible** to automate the deployment and configuration of a complete multi-tier application consisting of:

- Nginx Web Server
- Application Server
- PostgreSQL Database
- Redis Cache Server

The infrastructure follows Ansible's recommended project structure with reusable roles, templates, handlers, inventories, variables, and Ansible Vault.

---

# Architecture

                    +----------------------+
                    |   Ansible Control    |
                    |        Node          |
                    +----------+-----------+
                               |
                SSH Configuration & Deployment
                               |
      -------------------------------------------------
      |               |               |               |
      ▼               ▼               ▼               ▼

+-------------+ +---------------+ +---------------+ +--------------+
| Nginx       | | Application   | | PostgreSQL    | | Redis Cache  |
| Web Server  | | Server        | | Database      | | Server       |
+-------------+ +---------------+ +---------------+ +--------------+
        |               |
        | Reverse Proxy |
        +--------------►|

Application Server communicates with:

- PostgreSQL
- Redis

---

# Features

✔ Infrastructure as Code (IaC)

✔ Multi-tier architecture automation

✔ Agentless automation using SSH

✔ Modular Ansible Roles

✔ Secure secrets using Ansible Vault

✔ Idempotent playbooks

✔ Dynamic Nginx reverse proxy

✔ PostgreSQL configuration

✔ Redis installation

✔ Automatic handler execution

✔ Inventory-based deployment

✔ Role-based configuration

✔ Selective execution using Tags

✔ Easy scalability

---

# Technologies Used

- Ansible
- YAML
- SSH
- Nginx
- PostgreSQL
- Redis
- Linux
- Git
- Jinja2 Templates
- Ansible Vault

---

# Project Structure

```
ansible-multitier-automation/
│
├── ansible.cfg
├── inventory.ini
├── site.yml
│
├── group_vars/
│   ├── all.yml
│   └── vault.yml
│
├── roles/
│   ├── common/
│   ├── nginx/
│   ├── app/
│   ├── database/
│   └── cache/
│
├── templates/
├── handlers/
├── files/
├── README.md
└── .gitignore
```

---

# Prerequisites

Before running this project install:

- Ubuntu/Linux
- Python 3
- Ansible
- Git
- SSH Access
- PostgreSQL
- Redis
- Nginx

Install Ansible

```bash
sudo apt update

sudo apt install ansible -y
```

Verify installation

```bash
ansible --version
```

---

# Configuration

## Configure Inventory

Edit

```text
inventory.ini
```

Example

```ini
[webservers]
web01 ansible_host=192.168.1.10

[appservers]
app01 ansible_host=192.168.1.11

[dbservers]
db01 ansible_host=192.168.1.12

[cacheservers]
cache01 ansible_host=192.168.1.13
```

---

# Ansible Vault

Create encrypted secrets

```bash
ansible-vault create group_vars/vault.yml
```

Store

- Database Password
- Secret Keys
- API Keys

Example

```yaml
vault_db_password: ********
vault_secret_key: ********
```

Never commit

```
.vault_pass.txt
```

---

# Ansible Roles

## Common Role

Responsible for

- Package Updates
- Installing utilities
- Firewall configuration
- Time synchronization
- Base server configuration

---

## Database Role

Responsible for

- PostgreSQL Installation
- Database Creation
- Database User
- Database Permissions

---

## Cache Role

Responsible for

- Redis Installation
- Redis Configuration
- Redis Service

---

## Application Role

Responsible for

- Clone Application
- Install Dependencies
- Configure Environment Variables
- Run Application

---

## Nginx Role

Responsible for

- Install Nginx
- Configure Reverse Proxy
- Deploy Jinja2 Template
- Enable Site
- Reload Service

---

# Running the Playbook

Execute

```bash
ansible-playbook -i inventory.ini site.yml
```

---

# Run Specific Roles

Only configure Nginx

```bash
ansible-playbook site.yml --tags nginx
```

Database only

```bash
ansible-playbook site.yml --tags database
```

Application only

```bash
ansible-playbook site.yml --tags app
```

---

# Idempotency

This project follows Ansible's idempotent design.

Running the playbook multiple times will not make unnecessary changes.

Expected Result

```
changed=0
failed=0
```

---

# Handlers

Handlers automatically restart or reload services only when configuration files change.

Example

- Reload Nginx
- Restart PostgreSQL
- Restart Redis
- Restart Application

---

# Deployment Flow

1. Read Inventory
2. Connect using SSH
3. Load Variables
4. Decrypt Vault
5. Install Packages
6. Configure Servers
7. Deploy Application
8. Configure Database
9. Configure Redis
10. Configure Nginx
11. Reload Services
12. Validate Infrastructure

---

# Security Features

- SSH Authentication
- Encrypted Secrets
- Firewall Rules
- Principle of Least Privilege
- Idempotent Configuration
- Secure Variable Management

---

# Benefits

- Automated Deployment
- Faster Provisioning
- Repeatable Infrastructure
- Secure Secrets
- Reduced Human Error
- Production-ready Project Structure
- Easy Maintenance
- Scalable Infrastructure

---

# Screenshots

Add screenshots of

- Folder Structure
- Successful Playbook Execution
- Inventory File
- Nginx Running
- PostgreSQL Running
- Redis Running
- Ansible Vault
- GitHub Repository

---

# Future Improvements

- Docker Integration
- Kubernetes Deployment
- CI/CD using GitHub Actions
- Dynamic AWS Inventory
- Terraform Integration
- Monitoring with Prometheus
- Grafana Dashboard
- SSL using Let's Encrypt
- Multi-Environment Support
- Auto Scaling

---

# Learning Outcomes

Through this project, I learned

- Infrastructure as Code
- Configuration Management
- Ansible Playbooks
- Roles
- Inventory Management
- Ansible Vault
- Handlers
- Templates
- Tags
- Idempotency
- SSH Automation
- Reverse Proxy Configuration
- PostgreSQL Automation
- Redis Automation
- Production Infrastructure Design

---
