kke_lab_linux-group-create

There are specific access levels for users defined by the xFusionCorp Industries system admin team. Rather than providing access levels to every individual user, the team has decided to create groups with required access levels and add users to that groups as needed. See the following requirements:


a. Create a group named nautilus_sftp_users in all App servers in Stratos Datacenter.

b. Add the user mohammed to nautilus_sftp_users in all App servers. (create the user if not present already)

Answer
[root@stapp03 banner]# groupadd nautilus_sftp_users
[root@stapp03 banner]# useradd -G nautilus_sftp_users mohammed
[root@stapp03 banner]# id mohammed
uid=1002(mohammed) gid=1003(mohammed) groups=1003(mohammed),1002(nautilus_sftp_users)
