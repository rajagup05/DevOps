
##  Script Execution Permissions

`Task`: **Your task is to grant executable permissions to the `/tmp/xfusioncorp.sh` script on App Server 2. Additionally, ensure that all users have the capability to execute it.**

- used `ssh user2@server2` to login/SSH into the server.
- used `ls -l /tmp/xfusioncorp.sh` and found this file is owned by root.
- used `sudo su - to switch/login` as a root user.
- used  `chmod a+rwx /tmp/xfusioncorp.sh` to add execute permissions for all users.
- used `ls -l /tmp/xfusioncorp.sh` to confirm if all the permissions are added.
