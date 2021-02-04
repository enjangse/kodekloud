kke_lab_linux-haproxy-troubleshooting

xFusionCorp Industries has an application running on Nautlitus infrastructure in Stratos Datacenter. The monitoring tool recognised that there is an issue with the haproxy service on LBR server. That needs to fixed to make the application work properly.


Troubleshoot and fix the issue, and make sure haproxy service is running on Nautilus LBR server.


[root@stlb01 log]# service haproxy status -l
Redirecting to /bin/systemctl status  -l haproxy.service
● haproxy.service - HAProxy Load Balancer
   Loaded: loaded (/usr/lib/systemd/system/haproxy.service; disabled; vendor preset: disabled)
   Active: failed (Result: exit-code) since Sat 2021-01-23 16:14:42 UTC; 18s ago
  Process: 165 ExecStart=/usr/sbin/haproxy-systemd-wrapper -f /etc/haproxy/haproxy.cfg -p /run/haproxy.pid $OPTIONS (code=exited, status=1/FAILURE)
 Main PID: 165 (code=exited, status=1/FAILURE)

Jan 23 16:14:42 stlb01.stratos.xfusioncorp.com haproxy-systemd-wrapper[165]: haproxy-systemd-wrapper: executing /usr/sbin/haproxy -f /etc/haproxy/haproxy.cfg -p /run/haproxy.pid -Ds
Jan 23 16:14:42 stlb01.stratos.xfusioncorp.com haproxy-systemd-wrapper[165]: [ALERT] 022/161442 (166) : Proxy 'main': unable to find required default_backend: 'app'.



default_backend             app

#---------------------------------------------------------------------
# round robin balancing between the various backends
#---------------------------------------------------------------------
backend app
    balance     roundrobin
    server  app1 127.0.0.1:5001 check
    server  app2 127.0.0.1:5002 check
    server  app3 127.0.0.1:5003 check
    server  app4 127.0.0.1:5004 check
