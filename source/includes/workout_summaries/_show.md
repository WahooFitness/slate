## Get a Workout Summary

### How to download a file

The Workout Summary show endpoint will provide the url for the workout summary fit file. The workout summary fit file is an 'activity' type fit file and provides additional in-depth information on a recorded workout. In order to download the fit file
please copy the url listed under "file", then paste it into your browser or make a GET call to download the fit file.

> Sample Response:

``````json
{
    "id": 8297,
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
    "file": {
        "url": "https://server.com/4_Mile_Segment_.fit"
    },
    "fitness_app_id": 1002,
    "created_at": "2018-10-23T20:43:50.000Z",
    "updated_at": "2018-10-23T20:43:50.000Z"
}
```

Requires the `workouts_read` scope

Returns the workout summary object for a workout. When a workout is created, the workout summary will be empty until it is updated.

```shell
curl --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/workouts/:id/workout_summary
```

### HTTP Request

`GET https://api.wahooligan.com/v1/workouts/:id/workout_summary`
