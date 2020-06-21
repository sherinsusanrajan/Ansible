# Ansible

Playbooks are written in yaml language .yml extention. Yaml file begins with ---

Default location of **inventory or _host file_** is /etc/ansible/hosts

**_modules_** are like library 

Do you want to become root user at the target server? Use **become**

**_Task_** what action you want to perform, mention it nder tasks

_example_
---
-name: <description>
 hosts: all
 become: true

 tasks:
 - name: install nginx
   yum:
     name: nginx
     status: latest
 - name: start nginx
   service:
     name: nginx
     status: started
   
   
