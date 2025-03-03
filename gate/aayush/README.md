# SonarQube Quality Gates

| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|
| Aayush Verma|   03-03-2025              | v1          | Aayush Verma   | 03-03-2025   |  Internal Reviewer | Siddharth |

## Table of Contents

- [What is SonarQube](#what-is-sonarqube)
- [What are Quality Gates in SonarQube](#what-are-quality-gates-in-sonarqube)
- [Benefits of SonarQube Quality Gates](#benefits-of-sonarqube-quality-gates)
- [Types of quality gates in SonarQube](#types-of-quality-gates-in-sonarqube)
- [SonarQube Quality Gate Implementation](#SonarQube-Quality-Gate-Implementation)
- [Conclusion](#Conclusion)
- [Contact Information](#contact-information)
- [Reference Links](#reference-links)

## What is SonarQube

SonarQube is an open-source platform developed by SonarSource for continuous inspection of code quality. It performs automatic reviews using static code analysis to detect bugs, code smells, and security vulnerabilities across multiple programming languages. By providing comprehensive reports and visualizations.

## What are Quality Gates in SonarQube

SonarQube quality gates are predefined sets of conditions used to assess the quality of software code during its development lifecycle. These conditions typically include metrics such as code coverage, code duplications, coding standards compliance, and security vulnerabilities. Quality gates evaluate these metrics against predetermined thresholds. If the code meets these standards, the gate passes; if not, it fails. 

## Benefits of SonarQube Quality Gates

| Benefit                 | Description                                                                                   |
|-------------------------|-----------------------------------------------------------------------------------------------|
| Early Issue Detection   | Catch code quality issues early in development, offering prompt feedback.                      |
| Consistency             | Ensure consistent code quality across projects and teams.                                      |
| Automation              | Automate code evaluation against metrics like coverage and vulnerabilities, saving time.       |
| Best Practices          | Encourage adherence to coding standards, improving overall code quality.                       |
| Integration             | Seamlessly integrate with CI/CD pipelines for continuous monitoring and improvement.           |
| Decision Support        | Provide insights for project managers to assess code readiness, reducing deployment risks.     |


## Types of quality gates in SonarQube

- ### Default Quality Gate

    SonarQube's default quality gate, known as "Sonar way," is a set of predefined conditions designed to ensure code quality and maintainability. It typically includes criteria such as no new critical issues, a minimum percentage of code coverage by unit tests on new code, and limits on code duplication. Additionally, it enforces high ratings for maintainability, reliability, and security on new code.



| Metric                   | Condition                          | Default Value                                |
|--------------------------|------------------------------------|----------------------------------------------|
| **Code Coverage**        | Code Coverage on New Code          | Greater than 80%                             |
| **Duplicated Lines**     | Duplicated Lines on New Code       | Limited amount                               |
| **Reliability Rating**   | Reliability Rating on New Code     | no new blocker or critical issues        |
| **Security Rating**      | Security Rating or Hotspot on New Code | no new blocker or critical vulnerabilities |
| **Maintainability Rating** | Maintainability Rating on New Code | technical debt ratio <= 5%               |

 - ### Custom Quality Gate

    In SonarQube, you can create custom quality gates to tailor code quality checks according to your project's specific requirements. custom quality gates let you adjust metrics like code coverage, duplication and maintainability according to your project's needs.

## SonarQube Quality Gate Implementation

### 1. Login to SonarQube
- Open your SonarQube instance (e.g., `http://localhost:9000`).
- Login using your credentials.

<img width="1136" alt="Screenshot 2025-03-03 at 10 44 07 PM" src="https://github.com/user-attachments/assets/2fa77ee7-d4f7-470f-9cff-51389afb93d0" />


<img width="352" alt="Screenshot 2025-03-03 at 10 31 40 PM" src="https://github.com/user-attachments/assets/12b55346-24ec-491d-ba61-f0fd050e2def" />

<img width="1440" alt="Screenshot 2025-03-03 at 10 18 52 PM" src="https://github.com/user-attachments/assets/31fbde68-7dd1-4c7e-a45c-a2eb12355921" />

<img width="1136" alt="Screenshot 2025-03-03 at 10 46 55 PM" src="https://github.com/user-attachments/assets/c657787d-0c0c-4218-b1e4-3c58281a5ae8" />

<img width="1440" alt="Screenshot 2025-03-03 at 10 27 07 PM" src="https://github.com/user-attachments/assets/8f5ee8c4-2d2c-4bc1-8096-8aee7abb03dd" />

<img width="1440" alt="Screenshot 2025-03-03 at 10 26 10 PM" src="https://github.com/user-attachments/assets/1923516a-5b47-467b-8ef0-e37832c53d60" />

<img width="1424" alt="Screenshot 2025-03-03 at 10 22 51 PM" src="https://github.com/user-attachments/assets/6f7c63e8-0ce6-475e-a957-20399f537836" />









########################

<img width="1440" alt="Screenshot 2025-03-03 at 10 41 21 PM" src="https://github.com/user-attachments/assets/b7645c54-dfb1-411f-abc2-fdb356bbad9d" />

<img width="1440" alt="Screenshot 2025-03-03 at 10 17 26 PM" src="https://github.com/user-attachments/assets/7f4441e6-57c3-4707-a80d-6fea1c0f4c79" />



<img width="1424" alt="Screenshot 2025-03-03 at 10 22 51 PM" src="https://github.com/user-attachments/assets/1a6bc9fc-a8b1-4de5-bd4a-1edbd667f638" />



<img width="1440" alt="Screenshot 2025-03-03 at 10 27 07 PM" src="https://github.com/user-attachments/assets/a4e8e5f0-fbd3-428a-add7-3edf9a3a29cb" />



### 2. Go to Quality Gates
- Click on **Quality Gates** in the top menu.

<img width="1424" alt="Screenshot 2025-03-03 at 10 22 51 PM" src="https://github.com/user-attachments/assets/6f7c63e8-0ce6-475e-a957-20399f537836" />

### 3. Create or Edit a Quality Gate
- If you want to modify an existing Quality Gate (like **SonarWay**), click on it. Otherwise, click **Create** to create a new one.

<img width="332" alt="image" src="https://github.com/user-attachments/assets/0cb90da2-9d13-46c6-897f-ea92aa5a7519" />
<img width="1440" alt="Screenshot 2025-03-03 at 10 18 52 PM" src="https://github.com/user-attachments/assets/dd216e79-4596-4205-93a1-112344462216" />

- Give the gate a meaningful name if creating a new one.

<img width="1440" alt="Screenshot 2025-03-03 at 10 26 10 PM" src="https://github.com/user-attachments/assets/39227f71-8406-4990-9adf-72270365189d" />

<img width="356" alt="image" src="https://github.com/user-attachments/assets/1c38a1e7-7f9e-404e-8441-3af5fc034ef3" />

### 4. Add Conditions for Failing Quality Gate

#### Code Coverage:
- **Condition**: If **Code Coverage** is less than **80%**, the project should fail.
  
  **Add Condition**:
  - **Metric**: `Coverage`
  - **Operator**: `is less than`
  - **Value**: `80%`
  - **Status**: `Error` (This will fail the project if coverage is below 80%).

<img width="352" alt="Screenshot 2025-03-03 at 10 31 40 PM" src="https://github.com/user-attachments/assets/2694d64e-2554-41f1-b61f-18b92517f695" />
<img width="1440" alt="Screenshot 2025-03-03 at 10 32 38 PM" src="https://github.com/user-attachments/assets/afda38ba-cbc7-4cca-8bee-102e7aa34348" />


### 5. Apply Quality Gate to Your Project
- Once you have added the conditions, save the quality gate.
- Go to Project Administration > Quality Gate.
- From the dropdown, select the quality gate you just created or updated.
- Save the settings.

### 6. Test the Quality Gate
- Run the SonarQube analysis for your project to check if the quality gate fails based on these conditions:
```
  mvn clean verify sonar:sonar -Dsonar.qualitygate.wait=true -Dsonar.projectKey=<project.key>  -Dsonar.projectName='project.Name'  -Dsonar.host.url=http://localhost:9000  -Dsonar.token=<your_token>

```
- After the analysis, go to the SonarQube dashboard for your project.
- Check the Quality Gate status:
  - If any condition (e.g., Code Coverage < 90%, Reliability Rating = B, etc.) is not met, the project will show as Failed.

<img width="1440" alt="Screenshot 2025-03-03 at 10 41 21 PM" src="https://github.com/user-attachments/assets/d3c053e8-4e9c-4c01-ad45-da2f2c0265de" />


## addtional

<img width="1136" alt="Screenshot 2025-03-03 at 10 44 07 PM" src="https://github.com/user-attachments/assets/698e83f1-fc3a-45b1-9a43-8c048861d0dc" />
<img width="1136" alt="Screenshot 2025-03-03 at 10 46 55 PM" src="https://github.com/user-attachments/assets/f128a08d-8b27-4be9-83c5-e4ab02826e90" />


### Conclusion

SonarQube's quality gates help maintain high code standards by checking metrics like code coverage, security, and maintainability. The default "Sonar way" gate provides a solid foundation, while custom gates allow for flexibility. Quality gates detect issues early, ensure consistency, and integrate smoothly into CI/CD pipelines, making them essential for modern software development.

---

##  Contact Information


| **Name**       | **Email Address**        |
|----------------|--------------------------|
| Aayush Verma   | <aayush.verma@mygurukulam.co> |


## References

1. [SonarQube Official Documentation - Quality Gates](https://docs.sonarqube.org/latest/user-guide/quality-gates/)  
2. [Best Practices for Managing Code Quality](https://www.sonarsource.com/)  
3. [Continuous Integration and Quality Gates](https://martinfowler.com/)  
4. [SonarQube Community Forum](https://community.sonarsource.com/)  

