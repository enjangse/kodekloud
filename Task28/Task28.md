kke_lab_linux-local-yum
The Nautilus production support team and security team had a meeting last month in which they decided to use local yum repositories for maintaing packages needed for their servers. For now they have decided to configure a local yum repo on Nautilus Backup Server. This is one of the pending items from last month, so please configure a local yum repository on Nautilus Backup Server as per details given below.


a. We have some packages already present at location /packages/downloaded_rpms/ on Nautilus Backup Server.

b. Create a yum repo named epel_local and make sure to set Repository ID to epel_local. Configure it to use package's location /packages/downloaded_rpms/.

c. Install package httpd from this newly created repo.

root@stbkp01 yum.repos.d]# createrepo /packages/downloaded_rpms/
Spawning worker 0 with 28 pkgs
Spawning worker 1 with 27 pkgs
Workers Finished
Saving Primary metadata
Saving file lists metadata
Saving other metadata
Generating sqlite DBs
Sqlite DBs complete
Error moving final /packages/downloaded_rpms/repodata to old dir /packages/downloaded_rpms/.olddata

[root@stbkp01 yum.repos.d]# cat epel_local.repo
[epel_local]
name=Epel Local Repository Demo
baseurl=file:///packages/downloaded_rpms
enabled=1
gpgcheck=0
protect=1

yum repolist
