## Get all Workouts

```shell
curl --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/workouts
```

> Sample Response:

``````json
{
  "workouts": [
    {
      "id": 56519,
      "starts": "2015-08-12T09:00:00.000Z",
      "minutes": 12,
      "name": "Friday afternoon",
      "plan_id": null,
      "workout_token": "123",
      "workout_type_id": 40,
      "workout_summary": null,
      "created_at": "2018-10-23T20:41:55.000Z",
      "updated_at": "2018-10-23T20:41:55.000Z"
    }
  ],
  "total": 1,
  "page": 1,
  "per_page": 30,
  "order": "descending",
  "sort": "starts"
}
```

Requires the `workouts_read` scope

Returns all workouts for the authenticated user. The workout are always sorted by the starts field in descending order. By default the most recent 30 workouts are returned.  The per_page parameter can be used to adjust the number of workouts returned.

In the response the total attribute is the total number of workouts for the current user.


### HTTP Request

`GET http://api.wahooligan.com/v1/workouts`

### Query Parameters

Parameter | Type    | Required | Default | Description
--------- | ----    | -------- | ------- | -----------
page      | integer | no       | 1       | Used for pagination.
per_page  | integer | no       | 30      | Limits the number of workouts returned.
