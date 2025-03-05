## Update a Plan

```shell
curl --header "Authorization: Bearer users-token-goes-here"  -X PUT
  -d 'plan[file]=data:application/json;base64,<base64-encoded-plan-file>&
      plan[filename]=plan.json&
      plan[provider_updated_at]=2023-01-04T12:00:00.000Z'  https://api.wahooligan.com/v1/plans/5
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
  "provider_updated_at": "2023-01-04T12:00:00.000Z",
  "deleted": false,
  "updated_at": "2023-12-19T22:26:36.000Z",
  "created_at": "2024-01-05T05:18:21.000Z"
}
```

Requires the `plans_write` scope

Updates a plan that is in the library of the authenticated user.

### HTTP Request

`PUT https://api.wahooligan.com/v1/plans/:id`

### Query Parameters

Parameter                            | Type   | Required  | Description
---------                            | ----   | --------  | -----------
plan[file]                           | File   | yes       | Base64 encoded JSON file
plan[filename]                       | String | no        | The name of the plan file
plan[provider_updated_at]            | Date   | yes       | External date/time the file was updated externally
