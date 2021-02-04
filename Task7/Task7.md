kke_lab_linux-user-create

For security reasons the xFusionCorp Industries security team has decided to use custom Apache users for each web application hosted, rather than its default user. This will be theApache user, so it shouldn't use the default home directory. Create the user as per requirements given below:


a. Create a user named ravi on the App server 2 in Stratos Datacenter.

b. Set UID to 1477 and its home directory to /var/www/ravi.

--------------

[root@stapp02 steve]# useradd -m -d /var/www/ravi -u 1477 ravi
useradd: user 'ravi' already exists
[root@stapp02 steve]# id ravi
uid=1477(ravi) gid=1477(ravi) groups=1477(ravi)

cat /etc/passwd
ravi:x:1477:1477::/var/www/ravi:/bin/bash
