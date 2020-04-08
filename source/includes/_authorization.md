# Authorization

```shell
# With shell, you can append the requested scopes as a space separated list of values
curl "<base_url>/oauth/authorize?scope=profile_read+profile_write"
  -H "Authorization: Bearer <Token>"
```

Applications must only request permission for resources they intend to access or modify. You can choose which permission scopes your app will request either by setting the scopes for your app in the developer portal or by sending a space separated list of scopes as a parameter in the `oauth/authorize` request.

We support the following OAuth 2.0 permission scopes:


Scope | Description
---------- | -------
profile_read	| Access your user profile data
profile_write	| Update your user profile data
workouts_read	| Access your workout history 
workouts_write	| Update your workout history
offline_data    | Receive data even when the app is closed
