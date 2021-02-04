

kke_lab_linux-httpd-troubleshooting
xFusionCorp Industries utilizes monitoring tools to check the status of every service, application, etc. running on the systems. The monitoring system identified that Apache service is not running on some of the Nautilus Application Servers in Stratos Datacenter.


Identify the faulty Nautilus Application Servers and fix the issue. Also, make sure Apache service is up and running on all Nautilus Application Servers. Do not try to stop any kind of firewall that is already running.

Apache is running on 6200 port on all Nautilus Application Servers and its document root must be /var/www/html on all app servers.

Finally you can test from jump host using curl command to access Apache on all app servers and it should work fine. E.g. curl http://172.16.238.10:6200/




change listen to 6200
curl http://localhost:6200
Welcome to xFusionCorp Industries !


[sudo] password for steve:
[root@stapp02 steve]# service httpd status
Redirecting t

[Wed Jan 08 06:14:32.865753 2020] [autoindex:error] [pid 170] [client 127.0.0.1:57770] AH01276: Cannot serve directory /var/www/html/: No matching DirectoryIndex (index.html,index.php) found, and server-generated directory index forbidden by Options directive



[root@stapp02 var]# httpd -t
httpd: Syntax error on line 31 of /etc/httpd/conf/httpd.conf: ServerRoot must be a valid directory
autoindex.conf  php.conf
