## API ADMIN PASSWORD

### The issue
While looking at the API's source code, we found in `src/migrations/1572547308077-CreateAdminUser.ts` that the database the API is using was seeded with the admin user. Inside the database the password was hashed but in the source code it was written in plain text.  

### The fix
We decided to rewrite the two lines concerning the admin password and to fix the issue by storing the password's hash directly in the database.  

The encryption key removed from the source code, we can safely push the password's hash to gitlab.
The key is for now being stored directly on the server, we strongly recommend to set up a secret manager system like [Vault](https://www.vaultproject.io/) for the company that would be useful for a lot of use cases.