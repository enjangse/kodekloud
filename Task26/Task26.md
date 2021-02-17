kke_lab_linux-nginx-config

Nautilus system admin's team is planning to deploy a front end application for their backup utility on Nautilus Backup Server, so that they can manage the backups of different websites from a graphical user interface. They have shared requirements to set up the same; please accomplish the tasks as per detail given below:


a. Install Apache Server on Nautilus Backup Server and configure it to use 8083 port (do not bind it to 127.0.0.1 only, keep it default i.e let Apache listen on server's IP, hostname, localhost, 127.0.0.1 etc).

b. Install Nginx webserver on Nautilus Backup Server and configure it to use 8095.

c. Configure Nginx as a reverse proxy server for Apache.

d. There is a sample index file /home/index.html on Jump Host, copy that file to Apache's document root.

e. Make sure to start Apache and Nginx services.

f. You can test final changes using curl command, e.g curl http://<backup server IP or Hostname>:8095.

nginx Proxy
server {
    listen 80;
    location / {
        proxy_pass http://192.x.x.2;
    }
}
