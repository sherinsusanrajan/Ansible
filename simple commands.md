**Rebooting** ansible all -a "/sbin/reboot"

**Copy file** ansible all -m copy -a "src=/home/sherin dest=/home/tmp"

**Create User** ansible all -m user -a "name=testuser password=<encryptedpassword>"

**Remove User** ansible all -m user -a "name=testuser state=absent"

**Change file permission** ansible all -m file -a "dest=/home/sherin/file.txt mode=777"

**Install Package** ansible all -m yum -a "name=httpd state=latest"

**Start a service** ansible all -m service -a "name=httpd state=started"

**Stop a service** ansible all -m service -a "name=httpd state=stopped"
