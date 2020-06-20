# Ansible Installation

### Prerequisites

A RHEL EC2 instance 

### Installation steps:
Update your EC2 Instance --> yum update

Add a third party repository named EPEL (Extra Packages for Enterprise Linux)to get packages for Ansible 
```sh 
rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
```

Install Ansible
```sh 
yum install ansible -y 
```
Test by checking Ansible version 
```sh 
ansible --version
```

Create a new user for ansible administration & grant admin access to user (common user for Master and Slave)
```sh
useradd ansadmin
passwd ansadmin
# below command adds ansadmin to sudoers file. But strongly recommended to use "visudo" command if you are aware vi or nano editor. 
echo "ansadmin ALL=(ALL) ALL" >> /etc/sudoers
```

Using keybased authentication is advised. If you are still at learning stage use password based authentication (Master & Slave)
```sh 
# sed command replaces "PasswordAuthentication no to yes" without editing file 
 sed -ie 's/PasswordAuthentication no/PasswordAuthentication yes/' /etc/ssh/sshd_config
 service sshd restart
``` 
To enable passwordless authentication between master and slave generate key and for that login as ansadmin user on master and generate ssh key (Master)
```sh 
ssh-keygen
```
Copy this keys to all ansible client nodes (from Master)
```sh 
ssh-copy-id <target-server>
```
login to the client nodes from master by ssh clienthostname and it shouldnt ask for password after first attempt.

Update target servers information on /etc/ansible/hosts file (Master)
```sh 
echo "<target server IP>" > /etc/ansible/hosts
```
Run ansible command as ansadmin user it should be successful (Master)
```sh 
ansible all -m ping
```
