kke_lab_linux-mariadb-troubleshooting

There is a critical issue going on with the Nautilus application in Stratos DC. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that mariadb service is down on the database server.


Look into the issue and fix the same.

Problem
210117 23:49:53  InnoDB: Waiting for the background threads to start
210117 23:49:54 Percona XtraDB (http://www.percona.com) 5.5.61-MariaDB-38.13 started; log sequence number 0
210117 23:49:54 [Note] Plugin 'FEEDBACK' is disabled.
210117 23:49:54 [Note] Server socket created on IP: '0.0.0.0'.
210117 23:49:54 [ERROR] mysqld: Can't create/write to file '/var/run/mariadb/mariadb.pid' (Errcode: 13)
210117 23:49:54 [ERROR] Can't start server: can't create PID file: Permission denied
210117 23:49:54 mysqld_safe mysqld from pid file /var/run/mariadb/mariadb.pid ended
cat: .bash: No such file or directory


Answer
change ownhership /var/run/mariadb
chown -Rf mysql.mysql /var/run/mariadb
