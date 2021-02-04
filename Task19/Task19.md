The Nautilus production support team was trying to fix issues with their storage server. The storage server has a shared directory /web, which is mounted on all app servers at location /var/www/html so that whatever data they store on storage server under /web can be shared among all app servers. Somehow NFS server is broken and having some issues.


Identify the root cause of the issue and fix it to make sure sharing works fine among all app servers and storage server.

/web 172.16.238.10(rw,sync,no_subtree_check,no_root_squas,fsid=0)/web 172.16.238.11(rw,sync,no_subtree_check,no_root_squas,fsid=0)
/web 172.16.238.12(rw,sync,no_subtree_check,no_root_squas,fsid=0)


/web 172.16.238.10(rw,sync,no_subtree_check,no_root_squash,fsid=0)
/web 172.16.238.11(rw,sync,no_subtree_check,no_root_squash,fsid=0)
/web 172.16.238.12(rw,sync,no_subtree_check,no_root_squash,fsid=0)
#/web 172.16.238.10,172.16.238.11,172.16.238.12(rw,sync,no_subtree_check,no_root_squash,fsid=0)


[root@stapp02 steve]# mount -t nfs -o nfsvers=3 -v 172.16.238.15:/web /var/www/html
mount.nfs: timeout set for Fri Jan 29 10:55:32 2021
mount.nfs: trying text-based options 'nfsvers=3,addr=172.16.238.15'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 172.16.238.15 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=17
mount.nfs: trying 172.16.238.15 prog 100005 vers 3 prot UDP port 20048

kke_lab_linux-nfs-troubleshooting
