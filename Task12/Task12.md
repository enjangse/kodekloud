kke_lab_linux-enable-service-boot

As per details shared by the development team, the new application release has some dependencies on the back end. There are some packages/services that need to be installed on all app servers under Stratos Datacenter. As per requirements please perform the following steps:


a. Install nscd package on all the application servers.

b. Once installed, make sure it is enabled to start during boot.

Answer
- yum install nscd
- systemctl enable nscd.service
[root@stapp01 tony]# systemctl enable nscd.service
Created symlink from /etc/systemd/system/multi-user.target.wants/nscd.service to /usr/lib/systemd/system/nscd.service.
Created symlink from /etc/systemd/system/sockets.target.wants/nscd.socket to /usr/lib/systemd/system/nscd.socket.

[root@stapp01 tony]# service nscd start
Redirecting to /bin/systemctl start nscd.service
[root@stapp01 tony]# service nscd status
