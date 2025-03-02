# Proof of Concept: Installing Ansible


| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|
| Aayush Verma|   27-02-2025              | v1          | Aayush Verma   | 27-02-2025   |  Internal Reviewer | Siddharth |


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

## 4. Prerequisites

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

## 5. Workflow for Installing Ansible

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

```bash
ansible --version
```

## 6. Run-Time Dependencies

| Dependency       | Purpose |
|-----------------|---------|
| Python 3.x      | Required for executing Ansible scripts |
| SSH client      | Used for communication with Linux-based managed nodes |
| WinRM modules   | Required for managing Windows-based nodes |
| YAML support    | Enables Ansible to process playbooks |

## 7. Required Ports

| Environment               | Port  |
|---------------------------|-------|
| Linux-based managed nodes | 22 (SSH) |
| Windows-based managed nodes | 5985 (HTTP) / 5986 (HTTPS) (WinRM) |
| Control node internal communication | localhost |

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

For further inquiries, contact:

- **Name:** [Your Name]
- **Email:** [Your Email]
- **GitHub:** [Your GitHub Profile]

## 12. References

- [Official Ansible Documentation](https://docs.ansible.com/)
- [Ansible GitHub Repository](https://github.com/ansible/ansible)
- [Ansible Installation Guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)

