# Installing Ansible POC

![image](https://github.com/user-attachments/assets/50db375c-2482-4101-abfc-f187f57f5fb7)

| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|
| Aayush Verma|   27-02-2025              | v1          | Aayush Verma   | 27-02-2025   |  Internal Reviewer | Siddharth |


## **Table of Contents**

  1. [Introduction](#introduction)
  2. [Why Ansible](#1-why-ansible)
  3. [What is Ansible](#2-what-is-ansible)
  4. [Key-Components of Ansible](#3-key-components-of-ansible)
  5. [Run Time Dependencies](#4-run-time-dependencies)
  6. [Required Ports](#5-required-ports)
  7. [Prerequisites](#6-prerequisites)
  8. [Workflow For Installing Ansible](#7-workflow-for-installing-ansible)
        - [ Update System Packages ](#step-1-update-system-packages)
        - [ Install Ansible ](#step-2-install-ansible)
        - [ Verify Installation ](#step-3-verify-installation)
        - [ Initialize Ansible Configuration ](#step-4-initialize-ansible-configuration)
  9. [Benefits of Using Ansible](#8-benefits-of-using-ansible)
  10. [Best Practices](#9-best-practices)
  11. [Conclusion](#10-conclusion)
  11. [Contact Informatio](#11-contact-information)
  12. [References](#12-references)


## Introduction

This document provides a comprehensive guide on installing Ansible, covering the reasons to use it, its key components, prerequisites, installation workflow, dependencies, required ports, benefits, best practices, and references.

## 1. Why Ansible?

Ansible is an open-source automation tool used for configuration management, application deployment, and infrastructure as code (IaC). It simplifies IT automation by using YAML-based playbooks and requires no agent installation on managed nodes.

## 2. What is Ansible?

Ansible is a lightweight, agentless automation tool that leverages SSH for Linux systems and WinRM for Windows. It helps automate repetitive tasks such as server provisioning, configuration management, and software deployment.

## 3. Key Components of Ansible

- **Control Node:** The system where Ansible is installed and from which automation tasks are executed.
- **Managed Nodes:** The remote systems that Ansible configures.
- **Inventory:** A file defining the target hosts and their groups.
- **Modules:** Small programs executed on managed nodes to perform specific tasks.
- **Playbooks:** YAML files defining automation workflows.
- **Roles:** Reusable sets of tasks and configurations.


## 4. Run-Time Dependencies

| Dependency       | Purpose |
|-----------------|---------|
| Python 3.x      | Required for executing Ansible scripts |
| SSH client      | Used for communication with Linux-based managed nodes |
| WinRM modules   | Required for managing Windows-based nodes |
| YAML support    | Enables Ansible to process playbooks |

## 5. Required Ports

| Environment               | Port  |
|---------------------------|-------|
| Linux-based managed nodes | 22 (SSH) |
| Windows-based managed nodes | 5985 (HTTP) / 5986 (HTTPS) (WinRM) |
| Control node internal communication | localhost |


## 6. Prerequisites

| Requirement            | Details |
|------------------------|---------|
| **Control Node**      | Runs Ansible and manages all nodes |
| OS                    | Linux-based OS (Ubuntu, CentOS, RHEL, Amazon Linux, etc.) |
| Python                | Python 3.x installed (`python3 --version`) |
| Pip                   | `pip` installed (`pip3 --version`) |
| **Managed Nodes**     | Machines Ansible controls. SSH/WinRM should be enabled, and users must have execution permissions. |
| SSH Access            | Enabled for Linux-based systems |
| WinRM                 | Enabled for Windows-based systems |
| User Permissions      | Proper user permissions to execute tasks (sudo or root access) |

## 7. Workflow for Installing Ansible

### **Step 1: Update System Packages**

Run the following command based on your OS:

#### Ubuntu/Debian:

```bash
sudo apt update -y
```

#### CentOS/RHEL:

```bash
sudo yum update -y
```

### **Step 2: Install Ansible**

#### Ubuntu/Debian:

```bash
sudo apt install -y ansible
```

#### CentOS/RHEL:

```bash
sudo yum install -y epel-release
sudo yum install -y ansible
```

#### Amazon Linux:

```bash
sudo amazon-linux-extras enable ansible2
sudo yum install -y ansible
```

#### Alternative: Install via Python (for any Linux)

```bash
sudo apt install -y python3-pip || sudo yum install -y python3-pip
pip3 install --user ansible
```

### **Step 3: Verify Installation**

```bash
ansible --version
```

### **Step 4: Initialize Ansible Configuration**

To generate a default `ansible.cfg` file with all configurations disabled, run:

```bash
ansible-config init --disabled > ansible.cfg
```

### **Step 5: Initialize a New Ansible Role**

```bash
ansible-galaxy init role_name 
```

## **Step 6: Run playbook**

``` sh
ansible-playbook -i <inventory-file> <playbook-name>
```

## 8. Benefits of Using Ansible

| Benefit                 | Description |
|-------------------------|-------------|
| Agentless Architecture  | No need to install an agent on managed nodes |
| Simple & Human-Readable | Uses YAML-based playbooks for automation |
| Idempotency             | Ensures consistency by applying configurations only when necessary |
| Scalability             | Manages thousands of servers with a single playbook |
| Cross-Platform Support  | Works on various OS environments |

## 9. Best Practices

- Use **roles** to structure your Ansible projects.
- Maintain a **version-controlled inventory file**.
- Use **Jinja2 templates** for dynamic configurations.
- Encrypt sensitive data using **Ansible Vault**.
- Test playbooks in a **staging environment** before applying them to production.
- Follow **idempotency** principles to avoid unnecessary changes.

## 10. Conclusion

Ansible is a powerful and flexible automation tool that simplifies infrastructure management. By following best practices and structuring playbooks properly, organizations can achieve efficient and error-free automation.

## 11. Contact Information


| **Name**       | **Email Address**        |
|----------------|--------------------------|
| Aayush Verma   | <aayush.verma@mygurukulam.co> |


## 12. References

| **Link** | **Description** |
|------------------------------------------------------|------------------|
|[Official Ansible Documentation](https://docs.ansible.com/)|  Official Ansible Documentation |
|[Ansible Installation Guide](https://medium.com/@kadimasam/install-ansible-on-ubuntu-22-04-f5152edcbdce)|Ansible Installation Guide|
| [Ansible role](https://medium.com/@ngueaghotiodongrobertolandry/ansible-roles-7c46c82d13be) | Ansible role |
