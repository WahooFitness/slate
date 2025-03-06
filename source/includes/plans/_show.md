## Get a Plan

```shell
curl --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/plans/5
```

> Sample Response:

```json
{
  "id": 5,
  "user_id": 4,
  "name": "Special Plan",
  "description": "Warmup for 10 minutes, FTP ladder up, cool down for 5 minutes",
  "file": {
      "url": "https://cdn.wahooligan.com/wahoo-cloud/production/uploads/plan/file/RGpT2JYKbmHzqRu2WFHHvg/plan.json"
  },
  "workout_type_family_id": 0,
  "workout_type_location_id": 255,
  "external_id": "P0001",
  "provider_updated_at": "2023-01-01T12:00:00.000Z",
  "deleted": false,
  "updated_at": "2023-12-19T22:26:36.000Z",
  "created_at": "2023-12-19T22:26:36.000Z"
}
```

Requires the `plans_read` scope

Returns a plan from the library of the authenticated user.

### HTTP Request

`GET https://api.wahooligan.com/v1/plans/:id`


<aside class='notice'>
Plans can only be retrieved which were uploaded by the same app
</aside>
