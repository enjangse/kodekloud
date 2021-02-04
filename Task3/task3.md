kke_lab_linux-selinux
SELINUX installation task

The xFusionCorp Industries security team recently did a security audit of their infrastructure and came up with ideas to improve the application and server security. They decided to use SElinux for an additional security layer. They are still planning how they will implement it; however, they have decided to start testing with app servers, so based on the recommendations they have the following requirements:


Install the required packages of SElinux on App server 2 in Stratos Datacenter and disable it permanently for now; it will be enabled after making some required configuration changes on this host. Don't worry about rebooting the server as there is already a reboot scheduled for tonight's maintenance window. Also ignore the status of SElinux command line right now; the final status after reboot should be disabled.


Answer
1. Update repo
   yum repolist

2. Install package
   yum install policycoreutils policycoreutils-python setools setools-console setroubleshoot

3. Check the status and config
   sestatus #will show you selinux sestatus

   [root@stapp02 steve]# sestatus
   SELinux status:                 disabled
   [root@stapp02 steve]# getenforce
   Disabled


4. Disable selinux permanently , change on the configuration vi /etc/selinux/config
   and then I can not find the file configuration. Seems there something missing in here.
   you can check the missing config file, using this command.
   yum provides


root@stapp02 steve]# yum provides /etc/selinux/config
Loaded plugins: fastestmirror, ovl
Loading mirror speeds from cached hostfile
 * base: mirror.softaculous.com
 * extras: mirror.fra10.de.leaseweb.net
 * updates: mirror.softaculous.com
selinux-policy-3.13.1-268.el7.noarch : SELinux policy configuration
Repo        : base
Matched from:
Filename    : /etc/selinux/config



selinux-policy-3.13.1-268.el7_9.2.noarch : SELinux policy configuration
Repo        : updates
Matched from:
Filename    : /etc/selinux/config


 5. seems we are missing this file selinux-policy-3.13.1-268.el7_9.2.noarch : SELinux policy configuration
 lets install that package.
[root@stapp02 steve]# yum install selinux-policy


6. disable selinux, vi /etc/selinux/config
  change the status from permissive to disabled, on SELINUX status
  SELINUX=disabled
