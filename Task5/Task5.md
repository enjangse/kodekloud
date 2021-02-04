kke_lab_linux-user-nohome

The system admins team of xFusionCorp Industries has set up a new tool on all app servers, as they have a requirement to create a service user account that will be used by that tool. They are finished with all apps except for App 2 in Stratos Datacenter.


Create a user named siva in App Server 2 without a home directory.

[root@stapp02 steve]# useradd -M siva
[root@stapp02 steve]# ls /home/
ansible  steve
