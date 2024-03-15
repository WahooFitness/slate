## Delete a Plan

```shell
curl -X DELETE --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/plans/5
```

Requires the `plans_write` scope

Deletes a plan that is in the library of the authenticated user.

### HTTP Request

`DELETE https://api.wahooligan.com/v1/plans/:id`


<aside class="notice">
Workouts that are associated with a plan will not be deleted, but the workouts will lose their association with the plan.
</aside>
