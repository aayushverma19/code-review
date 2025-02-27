
# SonarQube AWS Infra
![1_tvWYZwZGRnXJPtt-X7lOoA](https://github.com/avengers-p7/Documentation/assets/156056344/95180069-054e-4980-8d90-dc7e3e856d8c)

|   Authors        |  Created on   |  Version   | Last updated by | Last edited on |
| -----------------| --------------| -----------|---------------- | -------------- |
| Aakash Tripathi | 30 Jan 2024   |     v1     | Aakash Tripathi | 03 Feb 2024    |


## Table of Contents

+ [Introduction](#introduction)
+ [Description](#description)
+ [Infrastructure Diagram](#infrastructure-diagram)
+ [SonarQube HA & DR](#sonarqube-ha--dr)
+ [Contact Information](#contact-information)
+ [References](#References)

***
## Introduction
This document shows an overview of our AWS Infra for [SonarQube](https://github.com/avengers-p7/Documentation/blob/main/Application_CI/Design/07-%20Sonarqube/README.md). This document presents a detailed AWS infrastructure diagram outlining the setup of SonarQube within the AWS ecosystem. 

***
## Description

* Users connect to the environment through the internet.
* Traffic is directed through public subnets and security groups.
* Private components have internet access via the NAT gateway.
* Secure access to private resources is facilitated by bastion instances.
* Components are deployed within Virtual Private Clouds.
* Load balancer is configured for SonarQube UI via Internet and can also be used for HA capabilaties if required. 


## Infrastructure Diagram


![Untitled Diagram (1)](https://github.com/avengers-p7/Documentation/assets/156056344/dff0b602-eaaa-427b-a793-e0db9441d902)



## SonarQube HA & DR 
High availability and cluster scalability are features of the Data Center Edition of Sonarqube. However, HA and DR can be implemented in Community Edition in AWS ecosystem. 

### High availability
Please refer [*High Availibility in SonarQube*](https://github.com/avengers-p7/Documentation/blob/main/Application_CI/Design/07-%20Sonarqube/HA/README.md) for detailed explaination.

![image](https://github.com/avengers-p7/Documentation/assets/156056444/f0b1ecbe-d9f1-4b6e-b2b3-c68429a59ddf)

### Disaster Recovery
Please refer [*Disaster Recovery in SonarQube*](https://github.com/avengers-p7/Documentation/blob/main/Application_CI/Design/07-%20Sonarqube/DR/README.md) for detailed explaination.

***

## Contact Information

|  Name                     |        	Email Address           |
| ------------              | --------------------------------|
| Aakash Tripathi              |  aakash.tripathi.snaatak@mygurukulam.co       |  

## References

|  Source                                                                                 |        Description                 |
| ------------                                                                            | -----------------------            |
| SonarQube Docs                                                                          | https://docs.sonarsource.com/sonarqube/latest/setup-and-upgrade/overview/       |  
| HA | https://docs.sonarsource.com/sonarqube/latest/setup-and-upgrade/configure-and-operate-a-cluster/ |
