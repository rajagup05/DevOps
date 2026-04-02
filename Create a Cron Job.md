
## Create a Cron Job

`Task`: 

* Install `cronie` package on all app servers and start `crond` service.
* Add a cron `*/5 * * * * echo hello > /tmp/cron_text` for `root` user.

- used `ssh user1@server1` to connect/login to server1.
- used `cat /etc/os-release` to check the type of linux OS, in this case it was centOS.
- used `sudo yum install cronie` to install all the necessary files, used yum as it is centOS.

