# **POC of configuration using ansible tool**

| **Author** | **Created on** | **Version** | **Last updated by**|**Last Edited On**|**Level** |**Reviewer** |
|------------|---------------------------|-------------|----------------|-----|-------------|-------------|
| Aayush Verma|   27-02-2025              | v1          | Aayush Verma   | 27-02-2025   |  Internal Reviewer | Siddharth |

## **Table of Contents**

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



## Step-by-step installation 


**Step 1: Dynamic Inventory Setup** 

```yaml
[defaults]

# some basic default values...


# Use AWS EC2 dynamic inventory for managing hosts
inventory      = aws_ec2.yml

# Disable SSH host key checking for convenience.
host_key_checking = False

# Specify the path to the private key file for SSH connections.
private_key_file = /path/to/private_key

Sets the remote user for SSH connections to 'ubuntu'
remote_user = ubuntu

[inventory]
# enable inventory plugins
enable_plugins = aws_ec2,
```
[Ansible config file link]()

> [!NOTE]
>Ensure that for dynamic inventory you have the necessary AWS credentials configured in [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) or an IAM role on the node. 


**Step 2:  AWS EC2 Inventory**

```yaml
---
plugin: aws_ec2
regions:
  - "us-east-1"
filters:
  tag:Type:
    - "sonarQube"
  instance-state-name : running
compose:
  ansible_host: private_ip_address
```

[SonarQube Dynamic Inventory link]()


1. `plugin: aws_ec2`: Specifies the use of the aws_ec2 plugin as the dynamic inventory source. This plugin is designed to fetch information about EC2 instances in AWS.
2. `regions: - us-east-1`: Indicates the AWS region(s) from which the dynamic inventory should fetch information.
3. `Server: "'sonarQube'`: Creates an Ansible group named sonar. This group includes EC2 instances where the tag named Type has a value of 'sonar'. You can tag all your sonarqube instances accordingly.
4. `instance-state-name: running`: Filters the inventory to include only running EC2 instances.  
5. `compose: ansible_host: private_ip_address`: Sets `ansible_host` to the instance's private IP for SSH access.

**Step 3: Create Ansible Role**
* Create a new Ansible role which should follow this directory structure:


image 

[SonarQube Ansible Role link]()

**Step 4: playbook.yml**
* This file is defining a set of tasks to be executed on hosts belonging to the ubuntu group.

```yaml
---
- hosts: all
  become: yes
  roles:
    - sonarQube-setup
```

[SonarQube Playbook link]()


**Step 5: Tasks**
1. `main.yml`: This main.yml file is acting as an orchestrator, importing tasks from the `sonarqube_debian.yml` file. This separation of tasks into different files is a good practice for better organization, especially when dealing with complex configurations or roles.

```yaml
---
# tasks file for sonarQube-setup
- name: install all dependence
  include_tasks: dependence.yml
  when: ansible_facts['os_family'] == 'Debian'
- name: postgresql user 
  include_tasks: useranddb.yml
  when: ansible_facts['os_family'] == 'Debian'
- name: Install SonarQube
  include_tasks: sonarqube.yml
  when: ansible_facts['os_family'] == 'Debian'
```

[SonarQube Tasks link]()

2. `Default` variables: This role comes with default values for several variables that have been used in the role. You can find these defaults in the `defaults/main.yml` file within the role directory.

```yaml
---
# defaults file for sonarQube-setup
sonarqube_install_dir: "/opt/sonarqube-{{ sonarqube_version }}"
sonarqube_service_name: "sonarqube"
sonarqube_download_url: "https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-{{ sonarqube_version }}.zip"
sonarqube_web_port: 9000
sysctl_config:
      - "vm.max_map_count=262144"
      - "fs.file-max=65536"
      - "ulimit -n 65536"
      - "ulimit -u 4096"
```

[SonarQube Defaults Variables link]()


## Role Defauls Variables 


| **Variable**                 | **Description** |
|------------------------------|---------------|
| `sonarqube_install_dir`      | Installation directory for SonarQube, dynamically set based on the version. |
| `sonarqube_service_name`     | The system service name for SonarQube. |
| `sonarqube_download_url`     | URL to download the specified SonarQube version. |
| `sonarqube_web_port`         | The port on which SonarQube will run (default: 9000). |
| `sysctl_config`              | System and user limits required for SonarQube. |
| `vm.max_map_count=262144`    | Sets the maximum number of memory map areas a process can use. |
| `fs.file-max=65536`          | Sets the maximum number of open file descriptors. |
| `ulimit -n 65536`            | Sets the maximum number of open file descriptors per process. |
| `ulimit -u 4096`             | Sets the maximum number of user processes. |

> [!NOTE]
> To customize the SonarQube installation based on your specific requirements, you can override these default values in main.yaml file in the vars directory of the role. 

3. `vars` variables: This role comes with static values for several variables that are defined in the `vars/main.yml` file within the role directory. These variables typically have higher precedence than those in the `defaults/main.yml` file."


| **Variable** | **Description** |
| ------------ | --------------- |
| `postgres_version` | Version of Postgresql to be installed as DB |
| `jdk_version` | Java Development Kit(JDK) version |
| `sonarqube_version` | Version of SonarQube to be installed |
| `sonarqube_download_url` | URL to download SonarQube zip file |
| `sonarqube_home` | Path to `SONARQUBE_HOME` directory |
| `sonarqube_web_port` | SonarQube webserver port |
| `sonarqube_user` | A linux and postgres user for sonarqube operations |
| `sonarqube_password` | Password for sonarqube postgres user |
| `sonarqube_db` | SonarQube schema in DB |
| `pgdg_repo_url` | Postgres repository URL |
| `pgdg_repo_version` | Postgres repository version based on distribution |
| `pgdg_key_url` | Postgres key URL |
| `postgresql_package_name` | Package to be downladed from Postgres repository |




3. `sonarqube_debian.yaml`: This file is included in the sonarqube/tasks/main.yml file


3 add file

**Step 6: Templates for Configuration**
We need to create two jinja2 templates :
* To configure SonarQube
* To set up SonarQube Service

1. `sonarqube.conf.j2` teamplate includes parameteters to configure SonarQube database and webserver

```yaml
# SonarQube configuration file

sonar.jdbc.url=jdbc:postgresql://localhost:5432/{{ sonarqube_db }}
sonar.jdbc.username={{ sonarqube_user }}
sonar.jdbc.password={{ sonarqube_password }}

sonar.web.host=0.0.0.0
sonar.web.port={{ sonarqube_web_port }}
```

2. `sonarqube.service.j2` template creates a service file for setting up `sonarqube.service`
```ini
[Unit]
Description=SonarQube service
After=syslog.target network.target

[Service]
Type=forking
ExecStart={{ sonarqube_home }}/current/bin/linux-x86-64/sonar.sh start
ExecStop={{ sonarqube_home }}/current/bin/linux-x86-64/sonar.sh stop
User={{ sonarqube_user }}
Group={{ sonarqube_user }}
Restart=always
LimitNOFILE=131072
LimitNPROC=8192

[Install]
WantedBy=multi-user.target
```

**Step 7: Playbook Execution**

* To set up Jenkins on your target servers, you will execute the Ansible playbook using the following command:

```bash
ansible-playbook -i aws_ec2.yml playbook.yml
```

> Additional Options
> 
> --limit: You can use this option to specify a subset of hosts from the inventory on which the playbook should be executed.
> 
> -e or --extra-vars: You can pass extra variables to the playbook using this option.


***
## Output
1.  **Host-level output**: Output for each host would indicate whether the playbook execution was successful or not.

![Screenshot 2024-02-05 022810](https://github.com/avengers-p7/Documentation/assets/156056344/3782928b-10f1-444d-b39f-fe87d5611313)


2. **SonarQube UI**: Once the playbook is executed successfully, SonarQube UI can be accessed at `http://sonarqube-server-ip:9000`

![Screenshot 2024-02-04 220309](https://github.com/avengers-p7/Documentation/assets/156056344/58434c15-38fb-436e-a44e-a40ce998f78c)


> [!NOTE]
> Make sure that the server security group allows traffic to default sonarqube port 9000. 

***

## Post-Installation Setup
* Open your web browser and navigate to `http://sonarqube-server-ip:9000`.
![Screenshot 2024-02-05 015518](https://github.com/avengers-p7/Documentation/assets/156056344/b67cb9bc-3bfb-4dad-bb9c-e1c92d5b7878)

* On your first login post installation, you can login using : `username:admin` & `password:admin`
  
  ![Screenshot 2024-02-05 023714](https://github.com/avengers-p7/Documentation/assets/156056344/d7ac25d2-8173-44ef-ab48-3fdf70253a6b)

* You'll be prompted to create a new password

  ![Screenshot 2024-02-05 023909](https://github.com/avengers-p7/Documentation/assets/156056344/ea953833-3f43-4e0b-9039-0792c1d21841)

* Once you set your new password . You're all set to begin using SonarQube

![Screenshot 2024-02-05 024023](https://github.com/avengers-p7/Documentation/assets/156056344/65412475-effc-4a17-bb5c-c9164bd366c4)


