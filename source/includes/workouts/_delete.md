## Delete a Workout

```shell
curl -X DELETE --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/workouts/:id
```

Requires the `workouts_write` scope

Deletes a workout that is owned by the authenticated user.

### HTTP Request

`DELETE https://api.wahooligan.com/v1/workouts/:id`
