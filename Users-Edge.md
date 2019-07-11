Create and edit users and return one or all system users.  This edge also allows setting an account or user's preferences and settings.  User management is part of the `/accounts/` edge.  

Note that deleted users are not returned in any GET calls.
 
#### GET:
`/account/users/`  
`/account/users/{USER_ID}/`  
Return a single user record or all users.

#### POST
`/account/users/{USER_ID}/`  
`/account/users/`  

Create or update a user record.
User data is sent using the following JSON or equivalent POST params

```
{
    "username": "UserName",
    "password": "Password",
    "first_name": "Johnny",
    "last_name": "Vegas",
    "timezone": "Europe/London",
    "role": "{ROLE_ID}"
}
```

### Delete User

Users are never actually removed from the database on deletion. Instead we set their `deleted_at` property to the time of deletion (in UTC). When deleting a user, the account's subscription `quantity` on Stripe is updated. 

#### POST
`/users/delete/{USER_ID}/` 

