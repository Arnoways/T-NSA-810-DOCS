## Root password vulnerability

### The issue
By trying common passwords, we realized that the root password on all 4 vms is __admin__.  
This user account grants every privileges on the machine, thus being a huge potential risk. It is known that __admin__ is amongst the most used passwords and can be crackable just using a brute force method.  

### The fix
We **must** modify it to a stronger password.  
We also think we should use ssh keys in order to log into our machines in order to have a safer way to connect to our information system. In addition, we should add some protection in order to harden our machines, here's a list of recommended actions:
- Change default ssh port to prevent some attacks that only target port 22.
- Install fail2ban, portsentry and rkhunter; these are useful tools to harden a linux server.  
- Restrain the ssh connection by private key only.
- Add iptables restrictions to limit connections to our private network only.
