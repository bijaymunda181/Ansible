## ✅ What is Ansible?

Ansible is an open-source IT automation tool used to automate:
</br>
Purpose
</br>
Meaning
</br>
Configuration Management
</br>
Install packages, update config files, manage services on servers automatically
</br>
Application Deployment
</br>

Deploy applications on many servers at once
Provisioning

Create servers in cloud (AWS, etc.) automatically
Orchestration
Manage multiple servers and their tasks in a sequence

## ✅ Why do we use Ansible?
Saves time by automating repeated tasks
Manage hundreds of servers from a single control machine
Agentless (only SSH is needed)
Very easy to learn (YAML-based playbooks)

## ✅ How Ansible Works (Simple Flow)
1. You have a Control Node (Ansible server)
2. You have Managed Nodes (client servers)
3. Ansible connects to the clients using SSH
4. It executes tasks using Playbooks (YAML files)

## ✅ Example Ansible Playbook
Copy code
Yaml
- name: Install Apache
  hosts: webservers
  tasks:
    - name: Install httpd
      yum:
        name: httpd
        state: present
📌 This playbook will install httpd on all servers in the webservers group.

## ✅ Where is Ansible Used?
Field
Usage
DevOps
CI/CD automation
Cloud
AWS, GCP, Azure provisioning
Linux Admin
Server configuration
Security
Patch management
Application Teams
Automated deployments

✅ Summary
Ansible is a powerful automation tool that helps you configure, manage, and deploy software across many servers easily using simple YAML files — without needing any agent.
📌 Next Learning Path (If You Want to Continue)
✔ Ansible Installation
✔ Inventory Files
✔ Playbooks
✔ Roles
✔ Real-time examples (Nginx, Tomcat, AWS modules)


## ✅ 1. What is Inventory in Ansible?

Inventory is a file where we store target server details (hosts).

Default inventory path: /etc/ansible/hosts

'Example inventory file (inventory)' :

[web]
</br>
192.168.1.10
</br>
192.168.1.20

[db]
</br>
192.168.1.30


Meaning:

We created two groups: web and db

Each group contains server IPs or hostnames

Ansible will run tasks on these servers

You can run a command on the group like:

ansible web -m ping -i inventory

## ✅ 2. What is a Module in Ansible?

A module is a function that performs a particular task on a server.

Example:

ping → check connection

yum / dnf → install package

service → start/stop services

copy → copy files

user → create user

Ad-hoc command with a module:

ansible web -m yum -a "name=httpd state=present" -i inventory


Meaning:

Install httpd on all servers in web group

## ✅ 3. What is a Playbook in Ansible?

A Playbook is a YAML file where we write multiple tasks (using modules) step-by-step for automation.

Example playbook (apache.yml):

---
- name: Install and start Apache
  hosts: web
  become: yes

  tasks:
  - name: Install httpd package
    yum:
    name: httpd
    state: present

  - name: Start httpd service
    service:
    name: httpd
    state: started
    enabled: yes


Run this playbook:

ansible-playbook apache.yml -i inventory

## ✅ SUMMARY (in one line)
Component	Purpose
Inventory	Where your servers are defined
Module	What action to perform (install, copy, start service, etc.)
Playbook	A script that contains multiple tasks using modules
