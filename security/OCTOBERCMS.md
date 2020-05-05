## OCTOBERCMS

### The issue
On machine-4 we noticed an octobercms container in error that was trying to reboot. After fixing the Dockerfile and using a docker-compose to use a real database for this service, we noticed that there was a `bootstrap.py` file that was used to setup admin access. The issue here is that the plain text password was written inside of it.

### The fix
After executing it, we removed this file form the container and from the machine. The admin user was created inside a mysql:5.7 database with persistent storage and the password is hashed inside the database. So the bootstrap file is not necessary anymore.  
The password should be stored in the credentials management solution we recommended in [this report](API_ADMIN_PASSWORD.md).  
In the meantime, it is being kept safe in a password manager until the solution is setup.
