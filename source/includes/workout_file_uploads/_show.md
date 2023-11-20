## Get a Workout File Upload

```shell
curl --header "Authorization: Bearer users-token-goes-here" https://api.wahooligan.com/v1/workout_file_uploads/:token
```
> Sample Response:

```json
{
    "id": 5,
    "user_id": 1,
    "token": "fRa2HvZ1N0WxuHw",
    "status": "pending",
    "time_zone": null,
    "workout_id": null,
    "workout_summary_id": null,
    "workout_file_id": null,
    "workout_name": null,
    "error": null,
    "target_workout_id": null,
    "created_at": "2018-10-23T20:43:50.000Z",
    "updated_at": "2018-10-23T20:43:50.000Z"
}
```
Requires the `workouts_write` scope

Returns the workout file upload object with the corresponding token. Since the processing of a Workout File Upload is asynchronous it may take a few seconds to a few hours before the upload has been processed. On average Workout File Uploads are processed in less than 5 seconds.

When the status is `complete` the file has completed processing and the `workout_id` and `workout_summary_id` fields will be populated with values that can be used to fetch those objects from the [workouts](#get-a-workout) and [workout_summary](#get-a-workout-summary) endpoints.

When the status is `error` the `error` attribute will contain additional information regarding the failure of the upload.

### HTTP Request

`GET https://api.wahooligan.com/v1/workout_file_uploads/:token`

### Upload Status

Status      | Description
----------- | ---------------------------------------
pending     | The file is waiting to be processed
in_progress | The file is currently being processed and should complete within 1-5 seconds
complete    | The file has successfully been processed
error       | There was an error processing the file
duplicate   | The uploaded file exactly matches a previously uploaded file

