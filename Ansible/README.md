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
This role is designed to automate the installation and configuration of SonarQube on target ubuntu servers. Whether you're setting up SonarQube for standalone code analysis or to integrate with continuous integration/continuous delivery solution, or other purposes, this role aims to simplify the process.


## Install Ansible

 To install Ansible on your system, please follow the link below for the Ansible Installation Guide. :- [Ansible Installation Guide]()

## Flow Diagram

* This diagram should help you visualize the sequence of tasks in the Ansible role for setting up SonarQube.

![image](https://github.com/user-attachments/assets/c591566e-eb68-4044-b7e3-326043f718b7)



***


## SonarQube 
SonarQube is a leading open-source platform for continuous inspection of code quality. It analyzes codebases, identifies bugs, security vulnerabilities, and code smells. Offering a comprehensive view of code health, SonarQube assists development teams in maintaining high-quality software, ensuring robust security, and fostering continuous improvement in codebases.


## Steps for creating Ansible role

[POC](link)

## Creating a Role

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
Ansible Roles offers a modular approach to automate infrastructure, making deployments efficient, consistent, and less error-prone.
This guide illustrates the process of deploying SonarQube in a development environment through Ansible. By adhering to these instructions, you can effectively provision and set up SonarQube.



##  Contact Information


| **Name**       | **Email Address**        |
|----------------|--------------------------|
| Aayush Verma   | <aayush.verma@mygurukulam.co> |


## References

| **Link** | **Description** |
|------------------------------------------------------|------------------|
| [Documentaion link](https://medium.com/@sanyal.s271/introduction-to-sonarqube-elevate-your-code-quality-and-security-1c42fd092bdb) | SonarQube  |
| [SonarQube Installation link](https://medium.com/@deshdeepakdhobi/how-to-install-and-configure-sonarqube-on-aws-ec2-ubuntu-22-04-c89a3f1c2447)| SonarQube Installation |
