kke_lab_linux-limits
On our Storage server in Stratos Datacenter we are having some issues where nfsuser user is holding hundred of processes, which is degrading the performance of the server. Therefore, we have a requirement to limit its maximum processes. Please set its maximum process limits as below:


a. soft limit = 75

b. hard_limit = 96

check limit process
ulimit -Sa
ulimit -Ha

ps aux | grep

/etc/security/limit.conf
nfsuser         soft    nproc   75
nfsuser         hard    nproc 96

https://access.redhat.com/solutions/61334
https://www.cyberciti.biz/faq/how-to-find-ulimit-for-user-on-linux/
https://www.unix.com/red-hat/181607-setting-ulimit-user.html
