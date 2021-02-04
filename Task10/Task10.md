kke_lab_linux-archive

On Nautilus storage server in Stratos DC there is a storage location /data which is used by different developers to keep their data (no confidential data). One of the developers ammar has raised a ticket and asked for a copy of his/her data present in /data/ammar directory on storage server. /home is an FTP location on storage server where developers can download their data. Below are the instructions shared by the system admin team to accomplish the task:


a. Make a ammar.tar.gz compressed archive of /data/ammar directory and move the archive to /home directory on Storage Server.

[root@ststor01 /]# tar -zcvf /home/ammar.tar.gz /data/ammar
tar: Removing leading `/' from member names
/data/ammar/
/data/ammar/nautilus1.txt
/data/ammar/nautilus3.txt
/data/ammar/nautilus2.txt


[root@ststor01 /]# tar -tvf  /home/ammar.tar.gz
drwxrwxrwx root/root         0 2021-01-12 18:08 data/ammar/
-rwxrwxrwx root/root        12 2021-01-12 18:08 data/ammar/nautilus1.txt
-rwxrwxrwx root/root        12 2021-01-12 18:08 data/ammar/nautilus3.txt
-rwxrwxrwx root/root        12 2021-01-12 18:08 data/ammar/nautilus2.txt
