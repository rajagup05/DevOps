
## Linux SSH Authentication

`Task:` **Set up a password-less authentication from user `thor` on jump host to all app servers through their respective sudo users.**

$ `ssh-keygen -t ed25519 -C "thor@jump-host"` 
=> Here, 
- I am creating a key in jump host server,
- `-t` indicates type of kry
- `-C` is used to specify a comment
