We have a backup management application UI hosted on Nautilus's backup server in Stratos DC. That backup management application code is deployed under Apache on the backup server itself, and Nginx is running as a reverse proxy on the same server. Apache and Nginx ports are 5001 and 8097, respectively. We have iptables firewall installed on this server. Make the appropriate changes to fulfill the requirements mentioned below:


We want to open all incoming connections to Nginx's port and block all incoming connections to Apache's port. Also make sure rules are permanent.

vi /etc/sysconfig/iptables
-A INPUT -p tcp -m state --state NEW -m tcp --dport 8092 -j ACCEPT
-A INPUT -p tcp -m state --state NEW -m tcp --dport 8082 -j DROP
