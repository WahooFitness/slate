# Deauthorize

```shell
# With shell, you can revoke access to an application
curl -X "DELETE" "<base_url>/v1/permissions"
  -H "Authorization: Bearer <Token>"
```

Application access can be revoked by sending a request to delete all permissions.


### HTTP Request

`DELETE https://api.wahooligan.com/v1/permissions`

### Deauthorization Features

In the Wahoo developer portal, there are several flags that can be set to control the deauthorization process. If these flags are set to true, the following actions will trigger when the above endpoint is called, or when a user revokes access to the application from their account settings.
- **Delete Upcoming Workouts**: This will delete incomplete workouts scheduled in the future. You should set this to true if you schedule workouts far in advance and want to clean up any excess data.
- **Delete Owned Plans**: This will delete all plans available to the user through your application. This is useful if you would like deauthorized users to lose access to any plans they have created or that you have shared with them.
