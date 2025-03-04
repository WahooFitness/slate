## Get All Routes

```shell
curl --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/routes
```

> Sample Response:

```json
{
  "routes":
  [
    {
      "id": 4,
      "user_id": 4,
      "name": null,
      "description": null,
      "file": {
        "url": "https://cdn.wahooligan.com/wahoo-cloud/development/uploads/route/file/Jj7dyVsMdeKQyih9C0S9SQ/testfile"
      },
      "workout_type_family_id": 1,
      "external_id": "1234",
      "provider_updated_at": "2023-12-19T22:26:36.000Z",
      "deleted": false,
      "start_lat": 33.975087,
      "start_lng": -85.105208,
      "distance": 123.0,
      "ascent": 2.5,
      "descent": 2.5,
      "updated_at": "2024-08-26T23:23:35.000Z",
      "created_at": "2024-08-26T23:23:35.000Z"
    },
    {
      "id": 5,
      "user_id": 4,
      "name": "awesome test",
      "description": null,
      "file": {
        "url": "https://cdn.wahooligan.com/wahoo-cloud/development/uploads/route/file/qRTvc2KTqb-YV6_gxUuB-A/testfile.fit"
      },
      "workout_type_family_id": 0,
      "external_id": "12340",
      "provider_updated_at": "2023-12-19T22:26:36.000Z",
      "deleted": false,
      "start_lat": 33.975087,
      "start_lng": -85.105208,
      "distance": 123.0,
      "ascent": 2.5,
      "descent": 2.5,
      "updated_at": "2024-08-26T23:33:15.000Z",
      "created_at": "2024-08-26T23:33:15.000Z"
    }
  ]
}
```

Requires the `routes_read` scope

Returns the routes for the authenticated user.

### HTTP Request

`GET https://api.wahooligan.com/v1/routes`

### Query Parameters

Parameter                            | Type   | Required  | Description
---------                            | ----   | --------  | -----------
external_id                          | String | no        | Limits the routes returned to the route that matches the external Id provided
