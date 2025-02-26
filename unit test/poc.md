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


## Steps of unit testing  

####  Cloning the Go Application
  First make a directory, then Within that directory clone the repository. 
  ```shell
  mkdir snatak_p7
  cd snatak_p7
  git clone https://github.com/OT-MICROSERVICES/employee-api.git  
  cd employee-api/routes/
  ```
  <img width="660" length="200" alt="Golang" src="https://github.com/avengers-p7/Documentation/assets/156056413/c12a898d-f9bd-4865-82f4-0eaf01f6e481">  

#### Install Prerequisites
   ```shell
  sudo apt update
  sudo snap install go --classic
  go version
  ```
   <img width="660" length="200" alt="Golang" src="https://github.com/avengers-p7/Documentation/assets/156056413/01d25209-8a1f-406a-9430-f12d47a94736"> 

#### Run the test
  * Open a terminal or command prompt, navigate to the directory containing your Go files, and run the tests using the go test command:
  ```shell
  go test
  ```
   <img width="660" length="200" alt="Golang" src="https://github.com/avengers-p7/Documentation/assets/156056413/51132d5d-afc0-4d56-8399-9ad784b243a9"> 

  * Run tests for the entire project, including all packages, you can run  
  ```shell
  go test ./...
  ```
  <img width="560" length="200" alt="Golang" src="https://github.com/avengers-p7/Documentation/assets/156056413/c42b610e-0d84-4ff1-baec-19dea948e931"> 

* To perform unit tests for the entire Go language repository and generate detailed output regarding the success and failure of test cases, you can use the go test command with the `-v (verbose) and -cover (test coverage)` flags. Here's the command:
  ```shell
  go test -v -cover ./...
  ```
  <img width="660" length="200" alt="Golang" src="https://github.com/avengers-p7/Documentation/assets/156056413/15ebafbc-aab4-4b14-b217-772eb64d666e"> 
  <img width="660" length="200" alt="Golang" src="https://github.com/avengers-p7/Documentation/assets/156056413/4f46a24f-66c1-4380-9e9e-10c930f36f9f"> 

#### Generating the report    
  * To generate a test coverage report in Go, you can use the built-in go test tool with the -coverprofile flag to generate a coverage profile, and then use the gohttps://github.com/avengers-p7/Documentation/blob/main/Application_CI/Design/04-%20Python%20CI%20Checks/UnitTesting.md tool cover command to generate an HTML coverage report.
  ```shell
  go test -coverprofile=coverage.out
  ```
  <img width="660" length="200" alt="Golang" src="https://github.com/avengers-p7/Documentation/assets/156056413/28755278-1660-4da5-ad2c-825f3ea2ab30"> 
  
  ```shell
  go tool cover -html=coverage.out -o coverage.html
  ```
  <img width="660" length="200" alt="Golang" src="https://github.com/avengers-p7/Documentation/assets/156056413/c8a09a6d-c41d-4405-a311-6753030e8cf8"> 

After running unit tests in Go using the standard testing framework provided by the `testing package`, we receive a comprehensive report confirming whether each unit, like a function or method, behaves correctly and generates the expected results.  
[**Coverage.htm**l](https://github.com/avengers-p7/Documentation/blob/main/Application_CI/Design/05-%20GoLang%20CI%20Checks/coverage.html)





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


