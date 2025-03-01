# Documentation on SonarQube Setup using Ansible role

<img width="1009" alt="Screenshot 2025-02-27 at 10 33 49 AM" src="https://github.com/user-attachments/assets/893aad70-ea79-4821-b06f-4c97306c3837" />


| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|
| Aayush Verma|   27-02-2025              | v1          | Aayush Verma   | 27-02-2025   |  Internal Reviewer | Siddharth |


**Table of Contents**

- [1. Introduction](#introduction)
- [2. What](#what)
- [3. Why](#why)
- [4. Steps for creating Ansible role](#Steps-for-creating-ansible-role)
                - [ 4.1 Creating a Role](#creating-a-role)
                - [**Folder Structure**](#folder-structure)
                - [Folder Structure](#folder-strucyure)
                - [Run playbook](#run-playbook)
   
5. [**Steps to run playbook**](#steps-to-run-playbook)
8. [**Conclusion**](#conclusion)
9. [**Contact Information**](#contact-information)
10. [**References**](#references)

## Introduction
Ansible is a powerful automation tool that lets you manage and configure your infrastructure efficiently. It uses a simple language called YAML to define tasks and playbooks.

## What 
Ansible Roles are a powerful way to organize and reuse automation tasks. They provide a standardized structure for grouping related tasks, variables, files, templates, and handlers. This modular approach makes your playbooks more manageable, reusable, and easier to maintain.


## Why Use Ansible Roles?
Ansible Roles are a powerful mechanism for organizing and reusing automation tasks.

| **Reason**                     | **Description**                                                                                       |
|--------------------------------|-------------------------------------------------------------------------------------------------------|
| **Simplify Complex Deployments** | Organizes tasks into reusable, modular components, making complex setups easier to manage.           |
| **Reduce Human Error**           | Ensures consistent execution of tasks through automation, reducing the chance of manual mistakes.     |
| **Accelerate Deployment Times**  | Speeds up deployments by reusing predefined tasks and configurations.                                |
| **Improve Consistency and Compliance** | Standardizes configurations, ensuring uniformity across environments and aiding regulatory compliance. |

## Pre-requisites

Before using this Ansible role to set up Jenkins, ensure that the following prerequisites are met:

1. **Ansible:**
   - Ansible must be installed on the control machine from which you plan to run the playbook. If Ansible is not installed, you can install it using this [link](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) . Version used for POC : ansible 2.10.8


### Ansible 
![ansible_logo_icon_169596](https://github.com/avengers-p7/Documentation/assets/156056344/21281851-6cfa-4b18-aee4-8812e193dc62)

Ansible is an open-source automation tool that simplifies and accelerates IT infrastructure management, application deployment, and task automation. Employing a declarative language, Ansible enables users to define desired states for systems and applications, automating complex workflows efficiently. With agentless architecture, it connects to remote systems over SSH or other protocols, making it versatile and easy to implement. 


2. **SSH Access to Target Servers:**
   - Ensure that you have SSH access to the target servers where SonarQube will be installed.

***



## Flow Diagram

* This diagram should help you visualize the sequence of tasks in the Ansible role for setting up SonarQube.

![Screenshot 2024-02-05 030520](https://github.com/avengers-p7/Documentation/assets/156056344/a90a22e7-1401-43ac-9487-7b19fc282764)

***

## SonarQube 
SonarQube is a leading open-source platform for continuous inspection of code quality. It analyzes codebases, identifies bugs, security vulnerabilities, and code smells. Offering a comprehensive view of code health, SonarQube assists development teams in maintaining high-quality software, ensuring robust security, and fostering continuous improvement in codebases.


# Steps for creating Ansible role

# Creating a Role

To create a new role, you can use the ansible-galaxy command:

``` sh
ansible-galaxy init role_name 
```


## Folder Structure

![image](https://github.com/user-attachments/assets/3424fd07-fd9b-464c-a0c3-c3dd526eb823)


## Run playbook

``` sh
ansible-playbook -i <inventory-file> <playbook-name>
```

## Conclusion
Ansible Roles offer a modular approach to automate infrastructure, making deployments efficient, consistent, and less error-prone.
This guide illustrates the process of deploying SonarQube in a development environment through Ansible. By adhering to these instructions, you can effectively provision and set up SonarQube within your AWS infrastructure.



##  Contact Information


| **Name**       | **Email Address**        |
|----------------|--------------------------|
| Aayush Verma   | <aayush.verma@mygurukulam.co> |


## References

| **Link** | **Description** |
|------------------------------------------------------|------------------|
| https://medium.com/@ngueaghotiodongrobertolandry/ansible-roles-7c46c82d13be |  |
| | |
