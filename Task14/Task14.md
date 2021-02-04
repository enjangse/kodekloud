kke_lab_linux-firewalld-easy

The Nautilus system admins team recently deployed a web UI application for their backup utility running on the Nautilus backup server in Stratos Datacenter. The application is running on port 5002. They have firewalld installed on that server. The requirements that have come up include the following:


Open all incoming connection on 5002/tcp port. Zone should be public.


[root@stbkp01 clint]# firewall-cmd --zone=public --add-port=5002/tcp
success

[root@stbkp01 clint]# firewall-cmd --zone=public --list-all
public
  target: default
  icmp-block-inversion: no
  interfaces:
  sources:
  services: dhcpv6-client ssh
  ports: 5002/tcp
  protocols:
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
