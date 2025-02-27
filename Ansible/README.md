# Documentation on SonarQube Setup using Ansible role

<img width="1009" alt="Screenshot 2025-02-27 at 10 33 49 AM" src="https://github.com/user-attachments/assets/893aad70-ea79-4821-b06f-4c97306c3837" />


| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|
| Aayush Verma|   27-02-2025              | v1          | Aayush Verma   | 27-02-2025   |  Internal Reviewer | Siddharth |


**Table of Contents**

1. [**Introduction**](#introduction)
2. [**What**](#what)
3. [**Why**](#why)
4. [**Steps for creating Ansible role**](#Steps-for-creating-ansible-role)
5. [**Folder Structure**](#folder-structure)
5. [**Steps to run playbook**](#steps-to-run-playbook)
8. [**Conclusion**](#conclusion)
9. [**Contact Information**](#contact-information)
10. [**References**](#references)

# Introduction
Ansible is a powerful automation tool that lets you manage and configure your infrastructure efficiently. It uses a simple language called YAML to define tasks and playbooks.

# What 
Ansible Roles are a powerful way to organize and reuse automation tasks. They provide a standardized structure for grouping related tasks, variables, files, templates, and handlers. This modular approach makes your playbooks more manageable, reusable, and easier to maintain.


# Why ?
Ansible Roles are a powerful mechanism for organizing and reusing automation tasks.

# Why Use Ansible Roles?

| **Reason**                     | **Description**                                                                                       |
|--------------------------------|-------------------------------------------------------------------------------------------------------|
| **Simplify Complex Deployments** | Organizes tasks into reusable, modular components, making complex setups easier to manage.           |
| **Reduce Human Error**           | Ensures consistent execution of tasks through automation, reducing the chance of manual mistakes.     |
| **Accelerate Deployment Times**  | Speeds up deployments by reusing predefined tasks and configurations.                                |
| **Improve Consistency and Compliance** | Standardizes configurations, ensuring uniformity across environments and aiding regulatory compliance. |


# Steps for creating Ansible role



# Folder Structure

![image](https://github.com/user-attachments/assets/3424fd07-fd9b-464c-a0c3-c3dd526eb823)


# Steps to run playbook

``` sh
ansible-playbook -i <inventory-file> <playbook-name>
```

# Conclusion
Ansible Roles offer a modular approach to automate infrastructure, making deployments efficient, consistent, and less error-prone.



#  Contact Information


| **Name**       | **Email Address**        |
|----------------|--------------------------|
| Aayush Verma   | <aayush.verma@mygurukulam.co> |


# References

| **Link** | **Description** |
|------------------------------------------------------|------------------|
| https://medium.com/@ngueaghotiodongrobertolandry/ansible-roles-7c46c82d13be |  |
| | |
