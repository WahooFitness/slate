# Routes

A route record holds navigation and other information relating to a specified course a user has selected. This includes but is not limited to a FIT file containing route data, a name, description, total distance, total ascent, and starting coordinates.

It is best practice to use the external_id and provider_updated_at fields to prevent duplicate records and ensure only a single copy of a route is uploaded to a user's library.

Routes imported by the Cloud API will not sync to the ELEMNT App. Routes will sync to the Wahoo App and directly to a ELEMNT bike computer.

