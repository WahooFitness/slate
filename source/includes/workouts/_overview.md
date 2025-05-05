# Workouts

A workout record holds information about a single workout event. A workout becomes a structured workout when it includes an association to a [plan](#plans).

### What is a daycode?

Daycodes can be used to specify a specific date a user would like a workout on without having to also tie the workout to a start time.
A daycode is an integer that is calculated based on how many days it has been since January 1st 2020 (daycode of 1), for example 1/1/2021 would have a daycode of 366 becuase 2020 was a leap year,
and 09/12/2024 would have a daycode of 1716.

### Workout Summary Update

Please be aware as of April 2025 only workout summaries that originated from Wahoo or the user's original App will be returned. 
Any workout summaries that originated from a third party app(Strava, Zwift) will no longer be returned and will show a 401 unauthorized error.
