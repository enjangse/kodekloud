kke_lab_linux-haproxy

There is a static website of Nautilus project running in Stratos Datacenter. Based on the infrastructure, they have already configured app servers and code is already deployed there. To make it work properly, they need to configure LBR server. There are number of options for that, but team has decided to go with HAproxy.


a. So install and configure HAproxy on LBR server using yum only and make sure all app servers are added to HAproxy load balancer. HAproxy must serve on default http port (Note: Please do not remove stats socket /var/lib/haproxy/stats entry from haproxy default config.).

b. You can access the website on LBR link—to do so click on the + button on top of your terminal, select option Select port to view on Host 1, and after adding port 80 click on Display Port.


Answer
1. yum install haproxy

vi /etc/haproxy/haproxy.cfg

#FrontEnd
frontend http_front
   bind *:80
   stats uri /haproxy?stats
   default_backend app
   mode http
   option forwardfor   # forward IP
   http-request set-header X-Forwarded-Port % [dst_port]   # forward port

#Backend
backend app
  balance roundrobin
  server app1 xxx.xxx.xxx.xxx port_number check
  server app2 xxx.xxx.xxx.xxx port_number check
