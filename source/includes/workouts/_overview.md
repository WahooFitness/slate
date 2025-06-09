# Workouts

A workout record holds information about a single workout event. A workout becomes a structured workout when it includes an association to a [plan](#plans).

### How to get workout information

To get information on a 'completed' workout, you can check the workout_summary attached to the workout record.
The workout_summary contains the results of the workout, such as distance, duration, and calories burned.
The parent workout object contains information about when a workout is scheduled or what sort of workout the end user was planning on completing.

### Limitations

Wahoo does not share completed workout data that originates from third-party applications. 
This means that if a user completes a workout using a third-party application, the workout will not be available in the Wahoo API.

### Fitness App Id
The fitness_app_id is an identifier for the application that created the workout.
This is used to identify the source of the workout data, such as Wahoo's own applications or third-party applications.
A fitness_app_id < 1000 indicates that the workout was created by a Wahoo application, while a fitness_app_id > 1000 indicates that the workout was created by a third-party application.

### What is a daycode?

Daycodes can be used to specify a specific date a user would like a workout on without having to also tie the workout to a start time.
A daycode is an integer that is calculated based on how many days it has been since January 1st 2020 (daycode of 1), for example 1/1/2021 would have a daycode of 366 becuase 2020 was a leap year,
and 09/12/2024 would have a daycode of 1716.

