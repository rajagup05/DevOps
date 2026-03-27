
### creation of a user with a non-interactive shell

`Task:` **Create a user named jim with a non-interactive shell on App Server 2.**

- used ssh username@server to login/SSH into the server.
- used sudo useradd jim -s /sbin/nologin to create a user jim using non-interactive shell (/sbin/nologin)

Here, -s represents the current shell I am using to run this command

- used grep jim /etc/passwd and got below output: jim:x:1001:1001::/home/jim:/sbin/nologin

