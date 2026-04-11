
## Day 9: MariaDB Troubleshooting

`Task:`
**There is a critical issue going on with the Nautilus application in Stratos DC. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that mariadb service is down on the database server.
Look into the issue and fix the same.**

- used $ `ssh user1@server1` to login/connect to server 1
- used $ `systemctl status mariadb` to check the status of mariaDB
```
mariadb.service - MariaDB 10.5 database server
     Loaded: loaded (/usr/lib/systemd/system/mariadb.service; disabled; preset: disabled)
     Active: inactive (dead)
       Docs: man:mariadbd(8)
             https://mariadb.com/kb/en/library/systemd/
```

As a basic step, I tried to stop and start the mariaDB service to see if it comes back online:
```
$ systemctl stop mariadb
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ====
Authentication is required to stop 'mariadb.service'.
Authenticating as: peter
Password: 
==== AUTHENTICATION COMPLETE ====
```

- used $ `systemctl start mariadb` to see if it resolves the issue but it failed and provided 2 commands to troubleshoot further.
```
==== AUTHENTICATING FOR org.freedesktop.systemd1.manage-units ====
Authentication is required to start 'mariadb.service'.
Authenticating as: peter
Password: 
==== AUTHENTICATION COMPLETE ====
Job for mariadb.service failed because a fatal signal was delivered causing the control process to dump core.
See "systemctl status mariadb.service" and "journalctl -xeu mariadb.service" for details.
```
- used $ `sudo tail -n 20 /var/log/mariadb/mariadb.log` to see the logs and error message
```
2026-04-09 13:12:43 0 [Note] InnoDB: Using AVX512 instructions
2026-04-09 13:12:43 0 [Note] mariadbd: O_TMPFILE is not supported on /var/tmp (disabling future attempts)
2026-04-09 13:12:43 0 [Note] InnoDB: Using Linux native AIO
2026-04-09 13:12:43 0 [Note] InnoDB: Initializing buffer pool, total size = 134217728, chunk size = 134217728
2026-04-09 13:12:43 0 [Note] InnoDB: Completed initialization of buffer pool
2026-04-09 13:12:43 0 [Note] InnoDB: Setting log file ./ib_logfile101 size to 100663296 bytes
2026-04-09 13:12:43 0 [Note] InnoDB: Renaming log file ./ib_logfile101 to ./ib_logfile0
2026-04-09 13:12:43 0 [Note] InnoDB: New log file created, LSN=45091
2026-04-09 13:12:43 0 [Note] InnoDB: 128 rollback segments are active.
2026-04-09 13:12:43 0 [Note] InnoDB: Removed temporary tablespace data file: "ibtmp1"
2026-04-09 13:12:43 0 [Note] InnoDB: Creating shared tablespace for temporary tables
2026-04-09 13:12:43 0 [Note] InnoDB: Setting file './ibtmp1' size to 12 MB. Physically writing the file full; Please wait ...
2026-04-09 13:12:43 0 [Note] InnoDB: File './ibtmp1' size is now 12 MB.
2026-04-09 13:12:43 0 [Note] InnoDB: 10.5.29 started; log sequence number 0; transaction id 20
2026-04-09 13:12:43 0 [Note] Plugin 'FEEDBACK' is disabled.
2026-04-09 13:12:43 0 [Note] InnoDB: Loading buffer pool(s) from /var/lib/mysql/ib_buffer_pool
2026-04-09 13:12:43 0 [Note] InnoDB: Buffer pool(s) load completed at 260409 13:12:43
2026-04-09 13:12:43 0 [Note] Server socket created on IP: '::'.
2026-04-09 13:12:43 0 [ERROR] mariadbd: Can't create/write to file '/run/mariadb/mariadb.pid' (Errcode: 13 "Permission denied")
2026-04-09 13:12:43 0 [ERROR] Can't start server: can't create PID file: Permission denied 
```

The error **Errcode: 13 "Permission denied" for the file /run/mariadb/mariadb.pid** means the MariaDB process doesn't have the rights to write its process ID file to that folder. This is a common issue after updates or manual configuration changes.
