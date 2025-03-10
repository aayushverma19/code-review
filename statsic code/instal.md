

## **Documentation of Static Code Anaylysis in Java CI Checks**


| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|
| Aayush Verma|  08-03-2025           | v1         | Aayush Verma   | 08-03-2025    |  internal review | komal jaiswal | 


## **Table of Content**
1. [Introduction](#introduction)
2. [Pre-requisites](#pre-requisites)
3. [What is Static Code Analysis?](#what-is-static-code-analysis)
4. [Why Use Static Code Analysis in CI?](#why-use-static-code-analysis-in-ci)
5. [Tools for Static Code Analysis](#tools-for-static-code-analysis)
6. [Comparison of Tools](#comparison-of-tools)
7. [POC](#poc)
8. [Conclusion](#conclusion)
9. [Contact Information](#contact-information)
10. [References](#references)


## **Introduction**


Continuous Integration (CI) is a key practice in software development where code changes are frequently merged, built, and tested. Static code analysis is a method to examine code without executing it, helping to find errors, bugs, and security issues. Combining CI with static code analysis ensures better code quality and fewer vulnerabilities in Java projects.
___
## **Pre-requisites**


| **Specification**      | **Details**         |
|-------------------------|---------------------|
| **Operating System**    | Ubuntu 22.04      |
| **CPU**                | 2 vCPU             |
| **Hard Disk**             | 20 GB              |
| **RAM**                | 4 GB               |

--- 

# Security ports

| **Port** | **Protocol** | **Source Side**    | **Destination Side** | **Use Case**                     |
|----------|--------------|--------------------|-----------------------|-----------------------------------|
| 22       | TCP          | Any                | Server               | SSH Access for remote login      |
| 80       | TCP          | Any                | Server               | HTTP traffic for web applications|
| 443      | TCP          | Any                | Server               | Secure HTTPS web traffic         |
| 5432     | TCP          | Application Server | Database Server      | PostgreSQL database access       |
| 9000     | TCP          | Any                | Server               |  SonarQube |


___

## **What is Static Code Analysis?**
Static code analysis is the process of reviewing code without running it. It helps detect errors, bugs, and security vulnerabilities by analyzing the code structure and patterns.

---

## **Why Use Static Code Analysis in CI?**

| **Reason**              | **Description**                                                                 |
|--------------------------|---------------------------------------------------------------------------------|
| **Early Bug Detection**  | Catch issues during development before runtime testing.                         |
| **Enhanced Security**    | Identify vulnerabilities early to reduce risks.                                |
| **Improved Code Quality**| Enforce coding standards and best practices.                                   |
| **Reduced Maintenance Costs** |	Clean code with fewer bugs reduces long-term maintenance expenses.|
|**Improved Team Collaboration** |	Consistent code style and fewer errors make teamwork easier and more effective.|

---

## **Tools for Static Code Analysis**  

| Tool         | Description  |  
|-------------|-------------|  
| ESLint      | A widely used tool for identifying and fixing problems in JavaScript and React code. Supports custom rules and integrations. |  
| Prettier    | Ensures consistent code formatting automatically. Works well alongside ESLint. |  
| SonarQube   | Provides deep code quality analysis, including security vulnerabilities and maintainability issues for JavaScript and TypeScript. |  
| Stylelint   | Lints CSS and SCSS, helping enforce consistent styling practices in React applications. |  

---



## **Comparison of Tools**


| **Feature**            | **ESLint**     | **Prettier**    | **SonarQube** | **Stylelint**  | 
|------------------------|---------------|----------------|---------------|---------------|
| **Language Support**   | JavaScript, TypeScript | JavaScript, TypeScript | Multi        | CSS, SCSS, LESS | 
| **Security Checks**    | Yes           | No             | Yes           | No            | 
| **Integration Options** | Extensive     | Extensive      | Extensive     | Moderate      |  
| **Ease of Use**        | Moderate      | High           | Moderate      | High          | 
| **Community**         | Large         | Large          | Large         | Medium        |
| **Cost**               | Free          | Free           | Paid/Free     | Free          |
| **User Interface**     | CLI-based     | CLI-based      | Advanced      | CLI-based     |



___
## **POC**
For a step-by-step guide on how to perform Static code Analysis in Java applications, check out our *Proof of Concept (POC)* document:  
[Click here to view the POC]()


## **Conclusion**

In this project, we are using SonarQube for static code analysis due to its ability to identify bugs, vulnerabilities, and code smells early in the development process. It ensures clean, secure, and maintainable code while integrating seamlessly with CI/CD pipelines, providing detailed reports and actionable insights to reduce technical debt and improve overall project reliability.



## **Contact Information**

| **Name**       | **Email Address**        |
|----------------|--------------------------|
| Aayush Verma   | <aayush.verma@mygurukulam.co> |


## **References**

| **Link** | **Description** |
|------------------------------------------------------|------------------|
| https://www.techtarget.com/whatis/definition/static-analysis-static-code-analysis/| Static Code Anlyasis |
|https://www.sonarsource.com/learn/static-code-analysis-using-sonarqube/| SonarQube for Static Code Analysis |
|https://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis/|List of Static Code Analysis Tools|
