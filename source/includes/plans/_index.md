## Get All Plans

```shell
curl --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/plans
```

> Sample Response:

```json
{
  "plans": 
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
}
```

Requires the `plans_read` scope

Returns the plans for the authenticated user.

### HTTP Request

`GET https://api.wahooligan.com/v1/plans`

### Query Parameters

Parameter                            | Type   | Required  | Description
---------                            | ----   | --------  | -----------
external_id                          | String | no        | Limits the plans returned to the plan that matches the external Id provided

