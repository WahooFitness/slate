## Create a Route

```shell
curl --header "Authorization: Bearer users-token-goes-here"  -X POST
  -d 'route[file]=data:application/vnd.fit;base64,<base64-encoded-route-file>&
      route[filename]=route.fit&
      route[external_id]=P0001&
      route[provider_updated_at]=2023-01-01T12:00:00.000Z
      route[name]=route name
      route[description]=fun test route
      route[workout_type_family_id]=0
      route[start_lat]=33.975087
      route[start_lng]=-85.105208
      route[ascent]=2.5
      route[descent]=2.5'  https://api.wahooligan.com/v1/routes
```

> Sample Response:

```json
{
  "id": 5,
  "user_id": 4,
  "name": "sample route",
  "description": null,
  "file": {
      "url": "https://cdn.wahooligan.com/wahoo-cloud/development/uploads/route/file/qRTvc2KTqb-YV6_gxUuB-A/testfile.fit"
  },
  "workout_type_family_id": 1,
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

Requires the `routes_write` scope.

Creates a route for the authenticated user

### HTTP Request

`POST https://api.wahooligan.com/v1/routes`

### Parameters

Parameter                            | Type   | Required  | Description
---------                            | ----   | --------  | -----------
route[file]                          | File   | yes       | Base64 encoded FIT file
route[filename]                      | String | no        | The name of the route file
route[external_id]                   | String | yes       | Unique external Id of the route
route[provider_updated_at]           | Date   | yes       | External date/time the file was updated externally
route[name]                          | String | yes       | The name of the route
route[description]                   | String | no        | A description of the route
route[workout_type_family_id]        | Integer| yes       | The workout type family - [Workout Type Family](#workout-type-family)
route[start_lat]                     | Float  | yes       | The start latitude of the route
route[start_lng]                     | Float  | yes       | The start longitude of the route
route[distance]                      | Float  | yes       | The total distance of the route(in meters)
route[ascent]                        | Float  | yes       | The total ascent of the route(in meters)
route[descent]                       | Float  | no        | The total descent of the route(in meters)

