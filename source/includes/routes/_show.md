## Get a Route

```shell
curl --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/routes/5
```

> Sample Response:

```json
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
```

Requires the `routes_read` scope

Returns a route from the library of the authenticated user.

### HTTP Request

`GET https://api.wahooligan.com/v1/routes/:id`


<aside class='notice'>
Routes can only be retrieved which were uploaded by the same app
</aside>
