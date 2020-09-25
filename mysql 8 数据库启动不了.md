```
The manual page at http://dev.mysql.com/doc/mysql/en/crashing.html contains
information that should help you find out what is causing the crash.
2020-09-24T15:23:36.454152Z mysqld_safe mysqld from pid file /var/lib/mysql/LAPTOP-TS6BKRV6.pid ended
2020-09-24T15:28:24.234909Z mysqld_safe Logging to '/var/log/mysql/error.log'.
2020-09-24T15:28:30.070432Z mysqld_safe Starting mysqld daemon with databases from /var/lib/mysql
2020-09-24T15:28:31.190137Z 0 [Warning] [MY-010139] [Server] Changed limits: max_open_files: 1024 (requested 8161)
2020-09-24T15:28:31.190160Z 0 [Warning] [MY-010142] [Server] Changed limits: table_open_cache: 431 (requested 4000)
2020-09-24T15:28:31.545874Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.0.21-0ubuntu0.20.04.4) starting as process 9269
2020-09-24T15:28:31.591773Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
2020-09-24T15:28:31.616301Z 1 [ERROR] [MY-012585] [InnoDB] Linux Native AIO interface is not supported on this platform. Please check your OS documentation and install appropriate binary of InnoDB.
2020-09-24T15:28:31.616735Z 1 [Warning] [MY-012654] [InnoDB] Linux Native AIO disabled.
2020-09-24T15:28:32.116694Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
2020-09-24T15:28:32.209329Z 1 [Warning] [MY-013021] [InnoDB] A transaction id in a record of table `mysql`.`collations` is newer than the system-wide maximum.
```


sudo apt remove --purge *mysql*
sudo apt remove --purge *mariadb*
sudo rm -rf /etc/mysql /var/lib/mysql
sudo apt autoremove
sudo apt autoclean