## Create a Workout File Upload

```shell
curl --header "Authorization: Bearer users-token-goes-here"  -X POST
  -d 'workout_file_upload[file]="data:application/vnd.fit;base64,RmFrZSBmaXQgZmlsZQ=="&
      workout_file_upload[filename]="workout_results.fit"&
      workout_file_upload[time_zone]="America/New_York"' https://api.wahooligan.com/v1/workout_file_uploads
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
    "workout_type_id": 40
}
```

Requires the `workouts_write` scope

Send the results of a workout to Wahoo for processing. This endpoint will attempt to process the uploaded FIT file and generate the correct workout and workout summary objects. If a workout object has already been created it is recommended to specify the `target_workout_id` within the request to ensure that the workout summary is associated with the correct workout.

<aside class="notice">
If the contents of the FIT file is modified after uploading it to Wahoo you must create a new Workout File Upload with the updated FIT file. It is not possible to modify a Workout File Upload.
</aside>

This endpoint will return a `workout_file_upload` object that will contain the current status of the upload.

### HTTP Request

`POST https://api.wahooligan.com/v1/workout_file_uploads`

### Parameters

Parameter                               | Type   | Required | Default | Description
---------                               | ----   | -------- | ------- | -----------
workout_file_upload[file]               | File   | yes      |         | Base64 encoded FIT File
workout_file_upload[filename]           | String | no       |         | The name of the workout file
workout_file_upload[time_zone]          | String | no       |         | The time zone where the FIT file was recorded
workout_file_upload[workout_name]       | String | no       |         | Name to use for the workout summary
workout_file_upload[target_workout_id]  | Number | no       |         | Wahoo Id of the workout this file should be associated with 
