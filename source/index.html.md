---
title: Wahoo Fitness API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://developers.wahooligan.com'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:

  - authorization

  - deauthorize

  - plans/overview
  - plans/plan_files
  - plans/create
  - plans/show
  - plans/update
  - plans/index
  - plans/delete

  - power_zones/overview
  - power_zones/create
  - power_zones/show
  - power_zones/update
  - power_zones/index
  - power_zones/delete

  - users/overview
  - users/show
  - users/update

  - workouts/overview
  - workouts/create
  - workouts/show
  - workouts/update
  - workouts/index
  - workouts/delete

  - workout_file_uploads/overview
  - workout_file_uploads/create
  - workout_file_uploads/show

  - workout_summaries/overview
  - workout_summaries/create
  - workout_summaries/show

  - webhooks/overview
  - webhooks/settings
  - webhooks/workout_summary
  
  - workout_types
  - errors

search: true
---

# Introduction

Welcome to the Wahoo Fitness OAuth2 API! You can use our API to access Wahoo Fitness OAuth2 API endpoints, which can get information on your  user profile and workout history stored in our cloud.

We have language bindings in Shell! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

## Data Model

This diagram shows how the data records are related within the API

[//]: # (Edit file here: https://drive.google.com/file/d/1cOpAiu_1DGkx8oLKtqP_uLMgk9d1x-vE/view?usp=sharing)
<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="531px" height="224px" viewBox="-0.5 -0.5 531 224"><defs/><g><rect x="0" y="0" width="200" height="60" rx="9" ry="9" fill="#000000" stroke="none" transform="translate(2,3)translate(100,0)scale(-1,1)translate(-100,0)" opacity="0.25"/><rect x="0" y="0" width="200" height="60" rx="9" ry="9" fill="#10739e" stroke="none" transform="translate(100,0)scale(-1,1)translate(-100,0)" pointer-events="all"/><g fill="#FFFFFF" font-family="Helvetica" font-weight="bold" text-anchor="middle" font-size="14px"><text x="99.5" y="35.5">User</text></g><rect x="308" y="160" width="220" height="60" rx="9" ry="9" fill="#000000" stroke="none" transform="translate(2,3)translate(418,0)scale(-1,1)translate(-418,0)" opacity="0.25"/><rect x="308" y="160" width="220" height="60" rx="9" ry="9" fill="#10739e" stroke="none" transform="translate(418,0)scale(-1,1)translate(-418,0)" pointer-events="all"/><g fill="#FFFFFF" font-family="Helvetica" font-weight="bold" text-anchor="middle" font-size="14px"><text x="417.5" y="195.5">Workout Summary</text></g><rect x="148" y="80" width="220" height="60" rx="9" ry="9" fill="#000000" stroke="none" transform="translate(2,3)" opacity="0.25"/><rect x="148" y="80" width="220" height="60" rx="9" ry="9" fill="#10739e" stroke="none" pointer-events="all"/><g fill="#FFFFFF" font-family="Helvetica" font-weight="bold" text-anchor="middle" font-size="14px"><text x="257.5" y="115.5">Workout</text></g><path d="M 100 60 L 100 100 Q 100 110 110 110 L 133.53 110" fill="none" stroke="#23445d" stroke-width="4" stroke-miterlimit="10" pointer-events="stroke"/><path d="M 143.53 110 L 133.53 115 L 133.53 105 Z" fill="#23445d" stroke="#23445d" stroke-width="4" stroke-miterlimit="10" pointer-events="all"/><path d="M 258 140 L 258 180 Q 258 190 268 190 L 293.53 190" fill="none" stroke="#23445d" stroke-width="4" stroke-miterlimit="10" pointer-events="stroke"/><path d="M 303.53 190 L 293.53 195 L 293.53 185 Z" fill="#23445d" stroke="#23445d" stroke-width="4" stroke-miterlimit="10" pointer-events="all"/></g></svg>

# Registration

Create a user account and register your app in our developer portal (https://developers.wahooligan.com). Your app can be set to 'Sandbox' or 'Production'. With 'Sandbox' apps you will be able to test and see your changes immediately but with very limited throughput. Production apps will have to go through a review process with Wahoo Fitness, and when approved your app can be released with a higher rate limit.

## Rate Limiting

> Rate limits and usage are included within each HTTP response header

```shell
  X-RateLimit-Limit: <limit_day>, <limit_hour>, <limit_5min>
  X-RateLimit-Remaining: <remaining_day>, <remaining_hour>, <remaining_5min>
  X-RateLimit-Reset: <seconds_until_reset>
```

> Sample header values for a successful response:

```shell
  X-RateLimit-Limit: 5000, 1000, 200
  X-RateLimit-Remaining: 4999, 999, 199
  X-RateLimit-Reset: 0
```

> Sample header values for a rate limited response:

```shell
  X-RateLimit-Limit: 5000, 1000, 200
  X-RateLimit-Remaining: 4800, 800, 0
  X-RateLimit-Reset: 300
```

The following chart shows how your app will be rate limited. If you require a higher throughput, please contact support to request an increase.

Interval                     | Sandbox Apps        | Production Apps
-----------                  | -----------         | ------------
Requests every 5 Min:        | 25                  | 200
Requests per Hour:           | 100                 | 1000
Requests per Day:            | 250                 | 5000

# Authentication

## Workflow

OAuth2 Uses the following authentication workflow. The goal is to obtain an **access_token** for a user that can be used for accessing Wahoo's API on the user's behalf. 

The Wahoo API does allow users to use the PKCE flow for authorization. If you would like to use the PKCE flow for your application please go to My Developer Apps -> select edit on your app and then select 'Yes' under the question asking if you would like to use PKCE for your application. If you would like to learn more about the PKCE flow please visit their documentation https://www.oauth.com/oauth2-servers/pkce/

Prior to starting the OAuth2 workflow please make sure the application has been created here(https://developers.wahooligan.com/applications) in order to obtain the client id and client secret.

**Step 1.** Send the user to Wahoo in order to login and grant access to your app using the following url:

    `https://<base_url>/oauth/authorize?client_id=<client_id>&redirect_uri=<redirect_uri>&scope=<scopes>&response_type=code`

**Step 2.** After successful authorization the user will be redirected back to your redirect_uri with a code.

    `<redirect_uri>?code=<code>`

**Step 3.** Send an HTTP POST to Wahoo with the code and your app's OAuth2 credentials and receive the access_token and refresh_token

    `https://<base_url>/oauth/token?client_secret=<client_secret>&code=<code>&redirect_uri=<redirect_uri>&grant_type=authorization_code&client_id=<client_id>`

**Step 4.** When the access_token expires after 2 hours you can use the refresh_token to get a new access_token and a new refresh_token

    `https://<base_url>/oauth/token?client_secret=<client_secret>&client_id=<client_id>&grant_type=refresh_token&refresh_token=<refresh_token>`

**Step 5.** You are now ready to send requests to our API by putting the new **access_token** within the following HTTP Header:

    `"Authorization": "Bearer <access_token>"`

Attribute           | Notes
-----------         | ----------- 
_base_url_:         | `api.wahooligan.com`
_client_id_:        | You can get your app's client_id from the developer portal.
_client_secret_:    | You can get your app's client_secret from the developer portal.
_redirect_uri_:     | You can set the redirect_uri for your app in the developer portal.
_scopes_:           | See [Authorization Scopes](#authorization)
_access_token_:     | Returned in Step 3; Used for API calls to view/manage user data.
_refresh_token_:    | Returned in Step 3; Used to refresh the access_token.
_expires_in_:       | Returned in Step 3; Indicates when the access_token will expire.
_code_challenge_:   | Required for PKCE in Step 1; A SHA256 hash value for the code verifier, must be Base64 encoded
_code_verifier_:    | Required for PKCE in Step 3; The original code verifier for the PKCE request 

**Our API returns strings for decimal data types in our responses. This is because our API uses JSON for responses and requests. Please be sure to use headers for Content-Type as application/JSON:**

**`Content-Type: application/json`**
