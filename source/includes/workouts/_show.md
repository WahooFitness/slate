## Get a Workout

```shell
curl --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/workouts/56519
```

> Sample Response:

```json
{
  "id": 56519,
  "starts": "2015-08-12T09:00:00.000Z",
  "minutes": 12,
  "name": "Friday Fun",
  "plan_id": null,
  "route_id": null,
  "workout_token": "123",
  "workout_type_id": 40,
  "workout_summary": {
      "id": 8297,
      "name": "Easy Ride",
      "ascent_accum": "450.00",
      "cadence_avg": "50.00",
      "calories_accum": "1500.00",
      "distance_accum": "24909.71",
      "duration_active_accum": "179.00",
      "duration_paused_accum": "95.25",
      "duration_total_accum": "275.00",
      "heart_rate_avg": "100.00",
      "power_bike_np_last": "150.00",
      "power_bike_tss_last": "304.90",
      "power_avg": "94.59",
      "speed_avg": "10.75",
      "work_accum": "1041480.00",
      "time_zone": "America/Denver",
      "manual": false,
      "edited": false,
      "fitness_app_id": 1002,
      "file": {
        "url": "https://server.com/4_Mile_Segment_.fit"
      },
      "created_at": "2018-10-23T20:43:50.000Z",
      "updated_at": "2018-10-23T20:43:50.000Z"
  },
  "created_at": "2018-10-23T20:41:55.000Z",
  "updated_at": "2018-10-23T20:41:55.000Z"
}
```

Requires the `workouts_read` scope

Returns a workout for the current authenticated user.

### HTTP Request

`GET https://api.wahooligan.com/v1/workouts/:id`
