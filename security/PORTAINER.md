## PORTAINER

### The issue
Lacking of admin credentials. The list containing user:passwords provided has one couple allowing us to enter in portainer. Unfortunately, this account has no rights.

### The fix
We couldn't find the password for the user with privileged rights, one solution might be to delete the volume containing portainer's data to trigger the admin password form again. 