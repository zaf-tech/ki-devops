# Git Lab

Document Version 1.0 
Date: 2024-12-21
Author:  [Talha Jilal] [ https://github.com/zaftechnologies ]
Copyright: 2024 Zaf Technologies Inc
Revision: 1.0

Copyright © 2024 Zaf Technologies Inc. All Rights Reserved.

<!-- ## Table of Contents
- [Pre-Req Create AWS Free Tier Linux VM ](4.Lab_1.md#Free_Free_tier_Linux_VM)
  - [Table of Contents](#table-of-contents)
  - [Intro](#intro)
  - [Install Git Client](#Install-Git)
  - [SSH Key](#Generate-SSH-Key)
  - [Sign Up on GitHub](#SignUP)
  - [Git commands](#Git-Commands) -->
 

 ## Table of Contents
- [Pre-Reqs](#pre-req)
- [Intro](#intro)
  - [What is Ansible](#what-is-ansible)
  - [Key Features of Ansible](#key-features-of-ansible)
- [Install Ansible](#install-git-client)
- [SSH Authentication Setup For Ansible](#SSH-Authentication-Setup)
- [Different Types of Ansible Commands](#different-types-of-ansible-commands)
- [Ansible Galaxy](#ansible-galaxy)

## Pre-Reqs

[Create AWS Free Tier Linux VM](4.Lab_1.md#Free_Free_tier_Linux_VM)

[Git Basics](12_Git_lab.md#Free_Free_tier_Linux_VM)


## Intro

### What is Ansible?

- Ansible is an open-source automation tool used for:

    1- Configuration management
    2- Application deployment
    3- IT orchestration
    4- Task automation
    5- It simplifies IT operations by automating repetitive tasks and ensuring systems are consistent and predictable.

### Key Features of Ansible

- Agentless:

    - No need to install software (agents) on managed nodes.
    - Communicates via SSH or WinRM.

- Simple YAML Syntax:

    - Uses human-readable YAML files for playbooks, making it easy to learn and write.

- Idempotent:

    - Ensures that tasks are applied only when necessary, avoiding unintended changes.

- Scalable and Flexible:

    - Manages hundreds of servers at once.
    - Works across various operating systems and platforms.

- Open Source:

    - Free to use with an active community for support.


## Install Ansible

- Let's start with single node ansible installation setup.

```
yum install -y ansible
``` 

Or 

```
amazon-linux-extras enable epel
yum install -y epel-release
yum install -y ansible
```

- Verification

```
ansible --version
```

## SSH Authentication Setup For Ansible

By default aws ec2 instance root login not prmitted run following commands to allow password authentication and root login. This practice is not recomended but just for learning purpose we are going to enable root user.

```
sed  -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config
echo "PermitRootLogin yes" >>  /etc/ssh/sshd_config
systemctl  reload sshd
```

- Create SSH-ky

```
ssh-keygen
```

Copy ssh key to target node.

```
ssh-copy-id localhost
```

- Verify SSH configuration

```
ssh localhost 
```

## Different Types of Ansible Commands

Ad-hoc commands are one-liner commands for quick tasks without needing playbooks.

- Create hosts file in ansible directory, and host can be one or more in one group or different groups.

```
echo "[all]" >> /etc/ansible/hosts
echo "[localhost]" >> /etc/ansible/hosts

```

Examples: 


```
ansible all -m ping
```

- Expected output.

```
localhost | SUCCESS => {
    "ansible_facts": {
        "discovered_interpreter_python": "/usr/bin/python3.9"
    },
    "changed": false,
    "ping": "pong"
}
```


- Few more userful examples 


```
ansible all -m shell -a "free -m"
```

- And use simple copy module and copy files on multiple nodes 

```
ansible all -m copy -a "src=/tmp/config.conf dest=/etc/myapp/config.conf"
```

- Sample use of command module. 

```
ansible all -m command -a "uptime"
```

## Ansible Galaxy

Roles in ansible are reusable sets of tasks. ( Cover Ansible Roles and Ansible collections topic in detail in separate lesson later)

- Install a role from Ansible Galaxy

```
ansible-galaxy install role_name
```

- Initialize a New Role 

```
ansible-galaxy init role_name
```

- Install a Collection:

```
ansible-galaxy collection install collection_name
```
- List Installed Collections
```
ansible-galaxy collection list
````
