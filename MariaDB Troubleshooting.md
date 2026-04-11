
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
