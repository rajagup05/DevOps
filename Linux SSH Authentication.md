
## Linux SSH Authentication

`Task:` **Set up a password-less authentication from user `thor` on jump host to all app servers through their respective sudo users.**

$ `ssh-keygen -t ed25519 -C "thor@jump-host"` 
=> Here, 
- I am creating a key in jump host server,
- `-t` indicates type of kry
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
