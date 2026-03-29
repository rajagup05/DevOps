
## Day 3: Secure Root SSH Access

`Task`: **Your task is to disable direct SSH root login on all app servers.**

- used ssh user3@server3 to login/SSH into the server
- used sudo -i to login as a root
- used sudo passwd root to create a new root passwd
- used nano /etc/ssh.sshd_config to oprn this file and edited PermitRootLogin no
- then to apply the changes restarted the sshd using command sudo systemctl restart sshd
- exited/came out of root and server
- then used ssh root@server3 and got: Permission denied, please try again.


tried same for ather 2 servers and disabled direct root login.

