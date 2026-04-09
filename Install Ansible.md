
## Day 8: Install Ansible

`Task:` Install ansible version `4.10.0` on `Jump host` using `pip3` only. Make sure Ansible binary is available globally on this system, i.e all users on this system are able to run Ansible commands.

- used $ `python3 –version` to see current python version

- used $ `pip3 –version` to see pip version

- used $ `sudo yum install python3-pip` to check and install the package if not exists:
``` 
Last metadata expiration check: 0:01:14 ago on Mon Apr  6 09:49:02 2026.
Package python3-pip-21.3.1-1.el9.noarch is already installed.
Dependencies resolved.
Nothing to do.
Complete!
```

- used $ `sudo pip3 install ansible==4.10.0` to install ansible of version `4.10.0` using `pip3`

- used $ `ansible –version` to check the ansible version
