# Golang CI Check | Unit Testing | POC

---

| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|
| Aayush Verma|   26-02-2025             | v1          | Aayush Verma   |26-02-2025    |  Internal Reviewer | Komal Jaiswal |

---
 ## Table of Contents
 
- [Introduction](#Introduction)
- [Pre-requisite](#Pre-requisite)
- [Performing Unit Testing](#Performing-Unit-Testing)
- [Conclusion](#Conclusion)
- [Contact](#Contact)
- [Refrence](#Refrence)

---

## Introduction

In this Document we are creating the POC of unit testing for the GoLang based API, to get the errors by performing the unit testing.


## Pre-requisite

install go link


## Run Time Dependency

| **Name** | **Version** | **Description** |
|------|---------|-------------|
| **go** | Greater then 1.21 | Application is built on this version only |


---

## Performing Unit Testing
 After cloning the repo to the system we run the below command 

 ```bash
go test $(go list ./... | grep -v docs | grep -v model | grep -v main.go) -coverprofile cover.out
```
This command will start executing unit tests.

<img width="959" alt="image" src="https://github.com/user-attachments/assets/4faf55f1-8ae5-40fc-87e2-44c73a17dc98" />


---

## Conclusion
We can say that Unit testing in GoLang ensures code correctness, identifies bugs early, improves code reliability, and promotes efficient debugging and maintenance. We are using Gotest tool to do unit testing in our project.

---

 ## Contact

| **Name**       | **Email Address**        |
|----------------|--------------------------|
| Aayush Verma   | <aayush.verma@mygurukulam.co> |
 
 ---

 ## Refrence

 | Link|Description|
  |:---:|:---:|

  | Tool              | Documentation Link                                                     |
|-------------------|------------------------------------------------------------------------|
|    |          |                                                                            |


