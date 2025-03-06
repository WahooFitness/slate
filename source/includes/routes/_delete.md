## Delete a Route

```shell
curl -X DELETE --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/routes/5
```

Requires the `routes_write` scope

Deletes a route that is in the library of the authenticated user.

### HTTP Request

`DELETE https://api.wahooligan.com/v1/routes/:id`
