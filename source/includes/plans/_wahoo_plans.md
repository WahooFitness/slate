
## Wahoo Plans

Developers can apply for access to Wahoo Plans. This entitlement will allow your app to access Wahoo plans from the API. To request access to the Wahoo Plans entitlement please send a request to `partnerships@wahoofitness.com`.

The Wahoo Plans entitlement enables the following: 

- Read Wahoo plan metadata from the plan endpoints. 
- Read Wahoo plan files.

### Wahoo Plan File Limitations

The Wahoo plan files are considered intellectual property of Wahoo Fitness and have the following additional limitations: 

- May only be retrieved during a specific window based on the `starts` time of the workout. 3 days before through 1 day after.
- The user must have an active Wahoo subscription plan.
- The user must authorize the `plans_read` scope.

The url for accessing the Wahoo Plan file will be found in the `file['url']` attribute of a `plan` object.

<aside class='notice'>
Your app must have the Wahoo Plans entitlement in order for your app to access Wahoo plans on behalf of the user.
</aside>
