# SonarQube Quality Gates

![image](https://github.com/user-attachments/assets/94f3f2ad-88ce-49bb-9ab7-912df40ef525)


| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|
| Aayush Verma|   03-03-2025              | v1          | Aayush Verma   | 04-03-2025   |  Internal Reviewer | Siddharth |

## Table of Contents

- [Introduction](#introduction)
- [What is SonarQube?](#what-is-sonarqube)
- [What are Quality Gates in SonarQube?](#what-are-quality-gates-in-sonarqube)
- [Benefits of SonarQube Quality Gates](#benefits-of-sonarqube-quality-gates)
- [Types of quality gates in SonarQube](#types-of-quality-gates-in-sonarqube)
- [SonarQube Quality Gate Implementation](#SonarQube-Quality-Gate-Implementation)
- [Best Practices for Quality Gates](#best-practices-for-quality-gates)
- [Common Issues and Troubleshooting](#common-issues-and-troubleshooting)
- [Conclusion](#Conclusion)
- [Contact Information](#contact-information)
- [Reference Links](#reference-links)



## SonarQube Quality Gate Implementation

### 1. Login to SonarQube
- Open your SonarQube instance (e.g., `http://localhost:9000`).
- Login using your credentials.

<img width="1440" alt="Screenshot 2025-03-03 at 10 17 26 PM" src="https://github.com/user-attachments/assets/7f4441e6-57c3-4707-a80d-6fea1c0f4c79" />

---

### 2. Go to Quality Gates
- Click on **Quality Gates** in the top menu.

<img width="1424" alt="Screenshot 2025-03-03 at 10 22 51 PM" src="https://github.com/user-attachments/assets/6f7c63e8-0ce6-475e-a957-20399f537836" />

---

### 3. Create or Edit a Quality Gate
- If you want to modify an existing Quality Gate (like **SonarWay**), click on it. Otherwise, click **Create** to create a new one.


<img width="1440" alt="Screenshot 2025-03-03 at 10 18 52 PM" src="https://github.com/user-attachments/assets/dd216e79-4596-4205-93a1-112344462216" />

---

- Give the gate a meaningful name if creating a new one.

<img width="1440" alt="Screenshot 2025-03-03 at 10 26 10 PM" src="https://github.com/user-attachments/assets/39227f71-8406-4990-9adf-72270365189d" />


#### **Step 1: Navigate to the Quality Gates Tab**
- Open SonarQube and log in as an administrator.
- Click on the **"Quality Gates"** tab in the top navigation bar.

#### **Step 2: Create a New Quality Gate**
- On the left side, click the **"Create"** button to add a new Quality Gate.
- A pop-up window will appear to enter details for the new Quality Gate.

#### **Step 3: Name the Quality Gate and Save**
- Enter a name for the Quality Gate (e.g., **"First Project"**) in the input field.
- Click on the **"Save"** button to create the Quality Gate.


---

### 4. Add Conditions for Failing Quality Gate

#### Code Coverage:
- **Condition**: If **Code Coverage** is less than **90%**, the project should fail.
  
  **Add Condition**:
  - **Metric**: `Coverage`
  - **Operator**: `is less than`
  - **Value**: `90%`
  - **Status**: `Error` (This will fail the project if coverage is below 90%).

<img width="352" alt="Screenshot 2025-03-03 at 10 31 40 PM" src="https://github.com/user-attachments/assets/2694d64e-2554-41f1-b61f-18b92517f695" />
<img width="1440" alt="Screenshot 2025-03-03 at 10 32 38 PM" src="https://github.com/user-attachments/assets/afda38ba-cbc7-4cca-8bee-102e7aa34348" />


1. **Conditions on Overall Code:**
  - A new condition is set for **Coverage**:
    - **Operator:** "is less than"
    - **Value:** "90.0%"

2. **Permissions Section:**
  - Shows a link to **"Grant permissions to a user or a group"** for managing this Quality Gate.

3. **Project Section** 
  - 1. Go to **Quality Gates** → Select your **Quality Gate**.  
  - 2. Scroll to the **Projects** section.  
  - 3. Click **"With"**, search for the project, and select it.  

---

### 5. Apply Quality Gate to Your Project
- Once you have added the conditions, save the quality gate.
- Go to Project Administration > Quality Gate.
- From the dropdown, select the quality gate you just created or updated.
- Save the settings.

---

### 6. Test the Quality Gate
- Run the SonarQube analysis for your project to check if the quality gate fails based on these conditions:
```
  mvn clean verify sonar:sonar -Dsonar.projectKey=<project.key>  -Dsonar.projectName='project.Name'  -Dsonar.host.url=http://localhost:9000  -Dsonar.token=<your_token>

```
> [!NOTE]
 >* sonar:sonar → Triggers the SonarQube analysis.
 >* -Dsonar.projectKey → Specifies the unique project identifier in SonarQube.
 >* -Dsonar.projectName → Defines the human-readable project name in SonarQube.
 >* -Dsonar.host.url → Sets the SonarQube server URL.
 >* -Dsonar.token → Provides authentication credentials via a token.



- After the analysis, go to the SonarQube dashboard for your project.
- Check the Quality Gate status:
  - If any condition (e.g., Code Coverage < 90%, Reliability Rating = B, etc.) is not met, the project will show as Failed.

<img width="1440" alt="Screenshot 2025-03-03 at 10 41 21 PM" src="https://github.com/user-attachments/assets/d3c053e8-4e9c-4c01-ad45-da2f2c0265de" />

---

### 7. SonarQube Quality Gate Analysis and Build Status

- **Successful Build**:

  This image shows a successful build where the SonarQube quality gate has been PASSED.

```
  mvn clean verify sonar:sonar -Dsonar.qualitygate.wait=true -Dsonar.projectKey=<project.key>  -Dsonar.projectName='project.Name'  -Dsonar.host.url=http://localhost:9000  -Dsonar.token=<your_token>

```
> [!IMPORTANT]
 >* -Dsonar.qualitygate.wait=true → Forces the build to wait until SonarQube completes analysis and returns a Quality Gate result.


<img width="1136" alt="Screenshot 2025-03-03 at 10 46 55 PM" src="https://github.com/user-attachments/assets/f128a08d-8b27-4be9-83c5-e4ab02826e90" />

---

- **Failed Build**

    This image shows a successful build where the SonarQube quality gate has been FAILURE.

```
  mvn clean verify sonar:sonar -Dsonar.qualitygate.wait=true -Dsonar.projectKey=<project.key>  -Dsonar.projectName='project.Name'  -Dsonar.host.url=http://localhost:9000  -Dsonar.token=<your_token>

```

<img width="1136" alt="Screenshot 2025-03-03 at 10 44 07 PM" src="https://github.com/user-attachments/assets/698e83f1-fc3a-45b1-9a43-8c048861d0dc" />

---

## Best Practices for Quality Gates

- Set realistic and achievable thresholds to avoid unnecessary failures.
- Regularly review and update quality gates to align with evolving project requirements.
- Integrate SonarQube with CI/CD pipelines for automated quality checks.
- Encourage developers to address issues at the early development stages.
- Use a combination of default and custom quality gates for flexibility.

---

## Common Issues and Troubleshooting

### Quality Gate Fails Unexpectedly
- Ensure the correct quality gate is applied to the project.
- Verify that the SonarQube analysis is completed successfully.
- Check logs for potential errors or misconfigurations.

### Coverage Not Detected
- Ensure test reports are correctly generated and included in the analysis.
- Verify proper integration of SonarQube with the build system (Maven, Gradle, etc.).

### Custom Quality Gate Not Applying
- Confirm that the custom quality gate is assigned to the project.
- Restart the SonarQube server if necessary.

---

## Conclusion

SonarQube's quality gates help maintain high code standards by checking metrics like code coverage, security, and maintainability. The default "Sonar way" gate provides a solid foundation, while custom gates allow for flexibility. Quality gates detect issues early, ensure consistency, and integrate smoothly into CI/CD pipelines, making them essential for modern software development.

---

##  Contact Information


| **Name**       | **Email Address**        |
|----------------|--------------------------|
| Aayush Verma   | <aayush.verma@mygurukulam.co> |


## References


| **Link**             | **Description**                                    |
|-----------------------------------------------------------------------------|--------------------------------------------------|
| [SonarQube Official Documentation - Quality Gates](https://docs.sonarqube.org/latest/user-guide/quality-gates/)   | Setup & Configuration  |
|[SonarQube Quality Gates](https://medium.com/@tarunprakash/quality-gates-a-must-have-thing-for-the-code-analysis-process-75b33d6b49dc)| Code Analysis Process|
|[Quality Gates Guide](https://articles.readytowork.jp/elevating-code-quality-ultimate-guide-to-integrate-sonarqube-with-circleci-for-effective-code-2cd9fcedb9ee)| Guide|
|[Best Practices for Managing Code Quality](https://www.sonarsource.com/)  | Code Quality Tips |
