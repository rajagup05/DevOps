
## Day 5: SElinux Installation and Configuration

`Task`: 
**Install the required SELinux packages.  \
Permanently disable SELinux for the time being; it will be re-enabled after necessary configuration changes. \ 
No need to reboot the server, as a scheduled maintenance reboot is already planned for tonight. \
Disregard the current status of SELinux via the command line; the final status after the reboot should be disabled**

- Installed Required SELinux Packages using command: `sudo yum install -y policycoreutils policycoreutils-python-utils selinux-policy selinux-policy-targeted libselinux-utils setroubleshoot-server setools setools-console`
- To Permanently Disable SELinux, used command: `sudo vi /etc/selinux/config` to open the file  and Changed the SELINUX line to disabled: `SELINUX=disabled`

>   didn't changed SELINUXTYPE and let it be default to targeted.

- To verify Configuration used command: `cat /etc/selinux/config` to check the changes made.

> [!NOTE]
> As requested, a immediate reboot is not necessary; the disabled state will take effect upon the scheduled restart. 

