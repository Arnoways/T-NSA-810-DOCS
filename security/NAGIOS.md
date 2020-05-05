## NAGIOS XI

### The issue
On machine-3, we noticed a nagios container running. While investigating, we noticed that it was running a `bootstrap.py` script that was including the administrator username & password. The issue here is obvious as keeping plain text credentials in code is a bad practice. 

### The fix
We removed this script from the container and from the machine after executing it to make sure the admin setup was done. The password should be stored in the credentials management solution we recommended in [this report](API_ADMIN_PASSWORD.md).  
In the meantime, it is being kept safe in a password manager until the solution is setup.