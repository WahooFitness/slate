## Get Plans for Workout


```shell
curl --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/workouts/:workout_id/plans
```

> Sample Response:

```json
[
  {
    "id": 51848987,
    "user_id": 4,
    "name": "public api plan 1",
    "description": null,
    "file": {
      "url": null
    },
    "workout_type_family_id": 0,
    "workout_type_location_id": 0,
    "external_id": "public_1",
    "provider_updated_at": null,
    "deleted": false,
    "updated_at": "2025-02-13T00:00:00.000Z",
    "created_at": "2025-02-13T00:00:00.000Z"
  }
]
```

Since a workout can link to a specific plan (`plan_id`) or to an array of plan options (`plan_ids`) this endpoint will return a list of all plans for a workout in a single api call.

Requires the `plans_read` scope

Returns the plans for the workout id.

### HTTP Request

`GET https://api.wahooligan.com/v1/workouts/:workout_id/plans`

<aside class="notice">
Only plans created by your app will be returned unless your app has the <a href="#wahoo-plans">Wahoo Plans entitlement</a>.
</aside>
