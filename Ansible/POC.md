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
# enable inventory plugins, default: 'host_list', 'script', 'auto', 'yaml', 'ini', 'toml'
enable_plugins = aws_ec2, host_list, virtualbox, yaml, constructed, script, auto, ini, toml
```

> [!NOTE]
>Ensure that for dynamic inventory you have the necessary AWS credentials configured in AWS CLI or an IAM role on the node. 

**Step 2:  AWS EC2 Inventory**

```yaml
---
plugin: aws_ec2
regions:
  - your_aws_region

groups: 
  ubuntu: "'ubuntu' in tags.Type"
```

1. `plugin: aws_ec2`: Specifies the use of the aws_ec2 plugin as the dynamic inventory source. This plugin is designed to fetch information about EC2 instances in AWS.
2. `regions: - us-east-1`: Indicates the AWS region(s) from which the dynamic inventory should fetch information.
3. `sonar: "'sonar' in tags.Type"`: Creates an Ansible group named sonar. This group includes EC2 instances where the tag named Type has a value of 'sonar'. You can tag all your sonarqube instances accordingly.

**Step 3: Create Ansible Role**
* Create a new Ansible role which should follow this directory structure:

![Screenshot 2024-02-05 015834](https://github.com/avengers-p7/Documentation/assets/156056344/e06c6296-0cb2-4816-af3d-c639f6061a79)


**Step 4: playbook.yml**
* This file is defining a set of tasks to be executed on hosts belonging to the ubuntu group.

```yaml
---
- hosts: sonar
  become: yes
  gather_facts: yes 
  roles:
    - sonarqube
```
**Step 5: Tasks**
1. `main.yml`: This main.yml file is acting as an orchestrator, importing tasks from the `sonarqube_debian.yml` file. This separation of tasks into different files is a good practice for better organization, especially when dealing with complex configurations or roles.

```yaml
---
# tasks file for sonarqube
- include: sonarqube_debian.yaml
  when: ansible_facts['os_family'] == 'Debian'
```

2. `Default` variables: This role comes with default values for several variables that have been used in the role. You can find these defaults in the `defaults/main.yml` file within the role directory.

```yaml
---
# defaults file for sonarqube
   postgres_version: 15
   jdk_version: 17
   sonarqube_version: "9.6.1.59531"
   sonarqube_download_url: "https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-{{ sonarqube_version }}.zip"
   sonarqube_home: "/opt/sonarqube"
   sonarqube_web_port: 9000
   sonarqube_user: sonarqube
   sonarqube_password: Password
   sonarqube_db: sonarqube
   pgdg_repo_url: "https://apt.postgresql.org/pub/repos/apt"
   pgdg_repo_version: "{{ ansible_distribution_release }}"
   pgdg_key_url: "https://www.postgresql.org/media/keys/ACCC4CF8.asc"
   postgresql_package_name: "postgresql"
```
### Role Variables 
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

> [!NOTE]
> To customize the SonarQube installation based on your specific requirements, you can override these default values in main.yaml file in the vars directory of the role. 


3. `sonarqube_debian.yaml`: This file is included in the sonarqube/tasks/main.yml file

```yaml
---
    - name: Install Dependencies
      apt:
        name:
          - "openjdk-{{ jdk_version }}-jdk"
          - "unzip"
        state: present

    - name: Create PostgreSQL APT repository configuration
      ansible.builtin.copy:
        content: "deb {{ pgdg_repo_url }} {{ pgdg_repo_version }}-pgdg main\n"
        dest: "/etc/apt/sources.list.d/pgdg.list"

    - name: Import PostgreSQL repository signing key
      ansible.builtin.apt_key:
        url: "{{ pgdg_key_url }}"
        state: present

    - name: Update package lists
      ansible.builtin.apt:
        update_cache: yes

    - name: Install the latest version of PostgreSQL
      ansible.builtin.apt:
        name: "{{ postgresql_package_name }}-{{ postgres_version }}"
        state: latest
      async: 60
      poll: 60

    - name: Start and enable PostgreSQL service
      systemd:
        name: "postgresql"
        state: started
        enabled: yes

    - name: Create PostgreSQL user for SonarQube
      command: sudo -u postgres createuser {{ sonarqube_user }} --no-createdb --no-superuser --no-createrole
      tags: postgres_setup

    - name: Set password for PostgreSQL user SonarQube
      command: sudo -u postgres psql -c "ALTER USER {{ sonarqube_user }} WITH PASSWORD '{{ sonarqube_password }}';"
      tags: postgres_setup

    - name: Create PostgreSQL database for SonarQube
      command: sudo -u postgres createdb -O {{ sonarqube_user }} {{ sonarqube_db }}
      tags: postgres_setup

    - name: Grant privileges on the SonarQube database
      command: sudo -u postgres psql -c "GRANT ALL PRIVILEGES ON DATABASE {{ sonarqube_db }} TO {{ sonarqube_user }};"
      tags: postgres_setup

    - name: Create SonarQube user
      ansible.builtin.user:
        name: sonarqube
        createhome: no
        home: /opt/sonarqube
        shell: /bin/bash

    - name: Add vm.max_map_count and fs.file-max to sysctl.conf
      ansible.builtin.lineinfile:
        path: /etc/sysctl.conf
        line: "{{ item }}"
      loop:
        - "vm.max_map_count=524288"
        - "fs.file-max=131072"

    - name: Reload sysctl settings
      ansible.builtin.command:
        cmd: sysctl --system

    - name: Create 99-sonarqube.conf file
      file:
        path: /etc/security/limits.d/99-sonarqube.conf
        state: touch

    - name: Create 99-sonarqube.conf file with Config
      ansible.builtin.blockinfile:
        path: /etc/security/limits.d/99-sonarqube.conf
        block: |
          sonarqube - nofile 131072
          sonarqube - nproc 8192

    - name: Ensure SonarQube home directory exists
      file:
        path: "{{ sonarqube_home }}"
        state: directory
        owner: sonarqube
        group: sonarqube

    - name: Download and extract SonarQube
      get_url:
        url: "{{ sonarqube_download_url }}"
        dest: "/tmp/sonarqube-{{ sonarqube_version }}.zip"

    - name: Extract SonarQube archive
      unarchive:
        src: "/tmp/sonarqube-{{ sonarqube_version }}.zip"
        dest: "{{ sonarqube_home }}"
        remote_src: yes

    - name: Create a symbolic link to SonarQube home
      file:
        src: "{{ sonarqube_home }}/sonarqube-{{ sonarqube_version }}"
        dest: "{{ sonarqube_home }}/current"
        state: link

    - name: Create SonarQube system user
      user:
        name: sonarqube
        system: yes

    - name: Set ownership of SonarQube files
      file:
        path: "{{ sonarqube_home }}"
        state: directory
        owner: sonarqube
        group: sonarqube
        recurse: yes

    - name: Configure SonarQube
      template:
        src: sonarqube.conf.j2
        dest: "{{ sonarqube_home }}/current/conf/sonar.properties"

    - name: Create SonarQube service file
      template:
        src: sonarqube.service.j2
        dest: "/etc/systemd/system/sonarqube.service"

    - name: Reload systemd
      systemd:
        daemon_reload: yes

    - name: Start SonarQube service
      systemd:
        name: sonarqube
        state: started
        enabled: yes
```

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
