
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


**To change env variable of `editor`:**

- used `echo $EDITOR` to see the current default editor. It outputs blank means its either vim or VI.
- To change this editor environment variable, I used `export EDITOR=nano`

### `sudo -i` vs `sudo su -`

The `sudo -i` command is used to start an interactive root shell on a Linux system. While the standard `sudo` command runs a single command with elevated privileges, `sudo -i` (the interactive flag) logs you in as the root user, loading that user's environment, including their specific shell variables and home directory.  It typically requires your own user password, not the root password.

The `sudo su -` command is a way to gain a full root (superuser) terminal session in Linux. It combines the powers of `sudo` and `su -` to bypass the need for a root password, instead using your own user password to elevate to a persistent administrative shell. 

**How It Works:**

1. `sudo:` Temporarily grants you administrative privileges. The system checks if you are in the authorized list (the sudoers file) and asks for your user password.
2. `su:` Short for **substitute user.** When used alone, it attempts to switch you to the root user.
3. `-` (**The Hyphen**): This is critical. It tells the system to start a login shell, which completely resets the environment (PATH, home directory, shell variables) to match the root user's settings.
