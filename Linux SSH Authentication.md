
## Linux SSH Authentication

`Task:` **Set up a password-less authentication from user `thor` on jump host to all app servers through their respective sudo users.**

$ `ssh-keygen -t ed25519 -C "thor@jump-host"` 
=> Here, 
- I am creating a key in jump host server,
- `-t` indicates type of key
- `-C` is used to specify a comment

output of above commands will be as mentioned below:
```
Generating public/private ed25519 key pair.
Enter file in which to save the key (/home/thor/.ssh/id_ed25519): 
Created directory '/home/thor/.ssh'.
Enter passphrase for "/home/thor/.ssh/id_ed25519" (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in /home/thor/.ssh/id_ed25519
Your public key has been saved in /home/thor/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:ZihIiP+21jVIa2Ar+d6GP1eOni127q++OFatXpn3OuA thor@jump-host 
The key's randomart image is:
+--[ED25519 256]--+
|                 |
|..               |
|o .              |
| o .o ..         |
|  oo.+.oS  .     |
|  o...+oo o oo   |
|   oo+ . * o+..  |
|   .+o+ B++.E... |
|   oooo*+OO+. .o.|
+----[SHA256]-----+

```

$ `ssh-copy-id user2@server2` 
=> Here, I am copying the generated key in thor's server to user2's server.

Below is the output: 
```
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/thor/.ssh/id_ed25519.pub"
The authenticity of host 'server2 (IP_address)' can't be established.
ED25519 key fingerprint is SHA256:QxUfpVB36Ccq3XvBW6cZnU0Bhlvu5uo5euCJ1cpXDyE.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
user2@server2's password: 

Number of key(s) added: 1

Now try logging into the machine, with: "ssh 'user2@server2'"
and check to make sure that only the key(s) you wanted were added.

```

$ `thor@jump-host ~$ ssh steve@server2` \
**output:** `[steve@stapp02 ~]$`

=> after ocopying the key from thor's server to server2, SSH'ing would not ask for password.
