#    **POC of Static Code Anaylysis in Java CI Checks**

![image](https://github.com/user-attachments/assets/8107c96f-b45b-4b61-81cc-05f729a6f678)

| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|





---

## **Table of Content**

1. [Install PostgreSQL](#install-postgresql)
2. [Configure sonarqube](#configure-sonarqube)
3. [Accessing SonarQube](#accessing-sonarqube)
   - [Step1. Access SonarQube Web Interface](#step1-access-sonarqube-web-interface)
   - [Step2. Change Password](#step2-change-password)
4. [Static Code Analysis](#static-code-analysis)
   - [Step1. Go to SonarQube and select the project](#step1-go-to-sonarqube-and-select-the-project)
   - [Step2. Configure the Project](#step2-configure-the-project)
   - [Step3. Generate Token](#step3-generate-token)
   - [Step4. Run Analysis](#step4-run-analysis)
   - [Step5. Result](#step5-result)
5. [Conclusion](#conclusion)  
6. [Contact Information](#contact-information)  
7. [References](#references)



## Install Sonarqube
- Here we use Sonarqube for static code analysis.To install sonarqube on your system, please follow the link below for the Sonarqube Installation Guide. :-[sonarqube Installation Guide](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Rohit-SCRUM-77/Common/Software%20/Sonarqube/Installation/README.md)


## Configure sonarqube

- Sonarqube is used for static  code analysis. Please follow the link below for Sonarqube configuration. [sonarqube Configuration](https://github.com/snaatak-Zero-Downtime-Crew/Documentation/blob/Rohit-SCRUM-77/Common/Software%20/Sonarqube/Configuration/README.md)


## **Accessing SonarQube**


### **Step1. Access SonarQube Web Interface**

``` bash
http://100.26.240.39:9000
```

> [!NOTE]
>* The default username and password are admin and admin respectively.
>* Make sure that the server security group allows traffic to default sonarqube port 9000. 

<img width="737" alt="Screenshot 2025-03-01 at 11 09 46 PM" src="https://github.com/user-attachments/assets/d0e00a8c-f1b8-4cd7-84fb-2117feddfb7f" />


___

### **Step2. Change Password**


Update the default password after logging in.

<img width="1440" alt="Screenshot 2025-03-01 at 11 10 14 PM" src="https://github.com/user-attachments/assets/4214e0bb-630b-44e4-8a4d-612778c66191" />


___

## **Static Code Analysis**

## **Step1. Go to SonarQube and select the project**

<img width="1440" alt="Screenshot 2025-03-01 at 11 11 20 PM" src="https://github.com/user-attachments/assets/aeccab58-f9c9-4f50-8e46-1542883034df" />



![image](https://github.com/user-attachments/assets/4ee4a13d-74eb-4603-843a-1c45ace78c21)

___

## **Step2. Configure the Project**
 Prepare your project for analysis by configuring the necessary files<br/>

![image](https://github.com/user-attachments/assets/038f90ae-92d1-44ff-9ee6-afa780561bbc)

___
## **Step3. Generate Token**
Copy the generated token for authentication during analysis.<br/>


![image](https://github.com/user-attachments/assets/c90f31f1-7071-410f-94f1-cd384e6db8d8)
___


## **Step4. Run Analysis**
Execute the analysis on your project.<br/>

![image](https://github.com/user-attachments/assets/4e6dfb83-84ec-49a7-86d0-92c53d7a4a70)


___

## **Step5. Result**
Review the analysis results in the SonarQube interface.<br/>

![image](https://github.com/user-attachments/assets/c60a73d9-937e-4f70-a53d-af432db2130e)


___

## **Conclusion**.

In this project, we are using SonarQube for static code analysis due to its ability to identify bugs, vulnerabilities, and code smells early in the development process. It ensures clean, secure, and maintainable code while integrating seamlessly with CI/CD pipelines, providing detailed reports and actionable insights to reduce technical debt and improve overall project reliability
___

## **Contact Information**



___
## **References**

| **Link** | **Description** |
|------------------------------------------------------|------------------|
| https://www.bairesdev.com/blog/java-static-code-analysis-tools/| Static Code Anlyasis |
| https://www.baeldung.com/java-static-code-analysis-tutorial| Static Code Analysis tool |
