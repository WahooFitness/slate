# Plans

Plan records hold information pertaining to the structure of a [workout](#workouts) that can be played on Wahoo devices and applications. A plan record includes a file which holds details about the intervals and targets to be performed during a workout.

For Information regarding how to build your plan file see [Plan Files](#plan-files).

Wahoo uses a library data model approach for planned workouts. A user should only have a single copy of a plan that can then be referenced by multiple workout instances. As a result creating a planned workout is a two-step process: 

1. Create a plan record to place the plan in the user's library and receive a plan id.
2. Create (or update) a workout record with a reference to the plan id.

It is best practice to use the external_id and provider_updated_at fields to prevent duplicate records and ensure only a single copy of a plan is uploaded to a user's library.

<aside class="notice">
In order for a plan to be displayed in the ELEMNT app and bike computer/RIVAL, the plan must be attached to a workout that is scheduled for the current day through six days from the current day. 
</aside>
