## Ansible HTTPD Installation and Configuration Project
# Overview
This Ansible project is designed to automate the installation and configuration of the Apache HTTP Server (httpd) on target servers.
The project includes an inventory file, roles, loops, and conditions to make the deployment flexible and efficient.

# Prerequisites
Ensure that the following prerequisites are met before running the Ansible playbook:
1-Ansible installed on the control machine.
2-SSH access to the target servers with sudo privileges.
3-Inventory file containing the target server details.

# Project Structure
ansible-httpd-project/
|-- inventory/
|   |-- hosts
|-- roles/
|   |-- common/
|       |-- tasks/
|           |-- main.yml
|       |-- templates/
|           |-- httpd.conf.j2
|-- site.yml
|-- README.md

 inventory/hosts: Contains the inventory file with the details of the target servers.

 roles/common/tasks/main.yml: Defines the main tasks for the Ansible playbook, including the installation and configuration of httpd.

roles/common/templates/httpd.conf.j2: Jinja2 template file for the httpd configuration.

site.yml: The main Ansible playbook that includes tasks from the roles and manages the execution flow.

# Ansible Playbook Execution
1-Update the inventory/hosts file with the details of your target servers:

ini
[web_servers]
server1 ansible_ssh_host=192.168.1.101 ansible_ssh_user=user
server2 ansible_ssh_host=192.168.1.102 ansible_ssh_user=user

2-Customize the roles/common/templates/httpd.conf.j2 file if needed to match your specific httpd configuration requirements.

3-Run the Ansible playbook:
bash
ansible-playbook site.yml -i inventory/hosts

# Playbook Execution Flow
1-The playbook starts by gathering facts about the target servers using the gather_facts Ansible module.

2-The common role is executed, which includes the following tasks:
  *Installing httpd using the yum package manager.
  *Copying the Jinja2 template for httpd.conf to the target servers.
  *Configuring httpd with the template and restarting the service.
3-The playbook concludes with a summary of the executed tasks and any changes made.
