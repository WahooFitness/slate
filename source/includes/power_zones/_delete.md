## Delete a Power Zone

```shell
curl -X DELETE --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/power_zones/:id
```

Requires the `power_zones_write` scope

Deletes a power zone that is owned by the authenticated user.

### HTTP Request

`DELETE https://api.wahooligan.com/v1/power_zones/:id`

