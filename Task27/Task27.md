kke_lab_linux-web-security
uring a recent security audit, the application security team of xFusionCorp Industries found security issues with the Apache web server on Nautilus App Server 1 server in Stratos DC. They have listed several security issues that need to be fixed on this server. Please apply the security settings below:


a. On Nautilus App Server 1 it was identified that the Apache web server is exposing the version number. Ensure this server has the appropriate settings to hide the version number of the Apache web server.

b. There is a website hosted under /var/www/html/news on App Server 1. It was detected that the directory /news lists all of its contents while browsing the URL. Disable the directory browser listing in Apache config.

c. Also make sure to restart the Apache service after making the changes.

Answer

#Add this on the bottom file

     ServerTokens Prod

     ServerSignature Off

#disable indexes
<Directory “/var/www/html/news”>

     Options -Indexes +FollowSymLinks

     AllowOverride None

     Require all granted
#OR

#remove Indexes
<Directory “/var/www/html/news”>

     Options FollowSymLinks

     AllowOverride None

     Require all granted
