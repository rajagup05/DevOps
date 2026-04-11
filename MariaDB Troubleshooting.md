
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
