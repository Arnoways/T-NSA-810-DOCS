## PORTAINER

### The issue
Lacking of admin credentials. The list containing user:passwords provided has one couple allowing us to enter in portainer. Unfortunately, this account has no rights.
We know that portainer have two user :
1. soupeladmin: user account with priviledged rights
2. no_rights: the user account without rights
We also found the hash password of these accounts in the portainer volume, in this file : `/var/lib/docker/volumes/portainer_data/_data/portainer.db`. It is a bcrypt hash, so it is very difficult to crack it.

### The fix
We couldn't find the password for the user with privileged rights, one solution might be to delete the volume containing portainer's data to trigger the admin password form again. 