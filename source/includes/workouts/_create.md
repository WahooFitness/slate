## Create a Workout

```shell
curl --header "Authorization: Bearer users-token-goes-here"  -X POST
  -d 'workout[name]="Friday fun"&
      workout[workout_token]=123&
      workout[workout_type_id]=40&
      workout[starts]=2015-08-12T09:00:00.000Z&
      workout[minutes]=12'  https://api.wahooligan.com/v1/workouts
```

> Sample Response:

```json
{
    "id": 56519,
    "starts": "2015-08-12T09:00:00.000Z",
    "minutes": 12,
    "name": "Friday Fun",
    "created_at": "2018-10-23T20:41:55.000Z",
    "updated_at": "2018-10-23T20:41:55.000Z",
    "plan_id": null,
    "route_id": null,
    "workout_token": "123",
    "workout_type_id": 40
}
```

Requires the `workouts_write` scope

Creates a workout for the authenticated user.

If you would like to create a planned structured workout please make sure to create a plan file
that can be attached to the workout. Documentation for creating a plan file can be found under the Plans tab.

### HTTP Request

`POST https://api.wahooligan.com/v1/workouts`

### Parameters

Parameter               | Type   | Required | Default | Description
---------               | ----   |----------| ------- | -----------
workout[name]           | String | yes      |         | The name of the workout
workout[workout_type_id]| Number | yes      |         | The type of the workout - [Workout Types](#workout-types)
workout[starts]         | Time   | yes      |         | Start time
workout[minutes]        | Number | yes      |         | Duration of the workout in minutes
workout[workout_token]  | String | yes      |         | Can be used by the application to identify the workout
workout[plan_id]        | Number | no       | null    | Id of the plan used in this workout
workout[day_code]       | Number | no       | null    | The number of days since 1/1/2020
workout[workout_summary]| Object | no       |         | Include summary results - [Workout Summary](#create-a-workout-summary)
workout[route_id]       | Number | no       | null    | Id of the route used in this workout
