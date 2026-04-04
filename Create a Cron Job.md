
## Create a Cron Job

`Task`: 

* Install `cronie` package on all app servers and start `crond` service.
* Add a cron `*/5 * * * * echo hello > /tmp/cron_text` for `root` user.

solution: 

- used `ssh user1@server1` to connect/login to server1.
- used `cat /etc/os-release` to check the type of linux OS, in this case it was centOS.
- used `sudo yum install cronie` to install all the necessary files, used yum as it is centOS.
- used `systemctl start crond` to crond service
- used `sudo su -` to change/switch to root user.
- used `crontab -e` to open a crontab vim editor
- and wrote: `*/5 * * * * echo hello > /tmp/cron_text` , saved and exited
- used `ls -l /tmp/cron_text` to check if `cron_text` file is created after 5 minutes.
- used `cat /tmp/cron_text` to see if output is ran after previous check for existence.


