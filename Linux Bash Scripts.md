
## Day 10: Linux Bash Scripts

`Task`: The production support team of xCorp Industries is working on developing some bash scripts to automate different day to day tasks. One is to create a bash script for taking websites backup. They have a static website running on App Server 3 in Datacenter, and they need to create a bash script named `beta_backup.sh` which should accomplish the following tasks. (Also remember to place the script under `/scripts` directory on App Server 3).

a. Create a zip archive named `xfusioncorp_beta.zip` of `/var/www/html/beta` directory.

b. Save the archive in `/backup/` on App Server 3. This is a temporary storage, as backups from this location will be cleaned on a weekly basis. Therefore, we also need to save this backup archive on Storage Server.

c. Copy the created archive to Nautilus Storage Server server in `/backup/` location.

d. Please make sure script won't ask for password while copying the archive file. Additionally, the respective server user (for example, tony in case of App Server 1) must be able to run it.

e. Do not use sudo inside the script.

> [!NOTE]
> The zip package must be installed on given App Server before executing the script. This package is essential for creating the zip archive of the website files. Install it manually outside the script.

**solution:** 

- used $ `ssh user3@server3` to ssh into the server3.
- used $ `cd /scripts/` to change the directory
- used $ `touch beta_backup.sh` to create a shell script under `/scripts/` directory/path.
- used $ `sudo chmod 755 /scripts/beta_backup.sh` to give execute permissions to current user for this script file.
- used $ `ls -l /scripts/` to list the details of this file with permissions and below is the output:
```
total 0
-rwxr-xr-x 1 banner banner 0 Apr 10 11:10 beta_backup.
```

- used $ `ls -l /var/www/html/beta/` =>
```
total 4
-rw-r--r-- 1 root root 38 Apr 10 11:03 index.html
```
- used $ `sudo yum install zip` to install zip  and found it already exists:
```
Last metadata expiration check: 1:33:38 ago on Fri Apr 10 09:42:46 2026.
Package zip-3.0-35.el9.x86_64 is already installed.
Dependencies resolved.
Nothing to do.
Complete!
```

- created script and viewed using command $ `cat /scripts/beta_backup.sh`, Here I am creating a zip/archive file of `/var/www/html/beta` directory, then used scp command to copy the archive file to storage server's /backup/ location, and finally running `bash test.sh` as we cant use sudo to provide execute permission for storage server user:
```
#!/bin/bash

zip -r /backup/xfusioncorp_beta.zip /var/www/html/beta

scp "/backup/xfusioncorp_beta.zip" "ssh natasha@ststor01:/backup/"

ssh natasha@ststor01 "bash test.sh"

echo "task complete" 

```
- additionally, created srcipt file in storage server as seen below, to provide sxecute perms to storage user to run the copied archive file:
```
#!/bin/bash 
sudo chmod u+x /backup/xfusioncorp_beta.zip
```

