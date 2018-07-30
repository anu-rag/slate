---
title: Taskplus API Reference

<!-- language_tabs: # must be one of https://git.io/vQNgJ -->

toc_footers:
  - <a href='https://travis-ci.com'>Taskplus API document</a>
  - <p>copywrite 2018 Node Technologies</p>

includes:
  - role
  - users
  - project
  - group
  - task
  - notification
  - errors

search: true
---

# Introduction

This is the very first documentation for Taskplus APIs. The request/response format is in json unless specifically mentioned otherwise. Still in development phase, anticipate for changes every now then.

# Making Requests

Since this application is a multi-tenant system, the tenant name is captured in the URL. So, the base URI would be: 
`http://[account_name].shyamasoft.com/api/[api_version]/`. Items inside `[]` are variable. The `[account_name]` is the tenant name and the `[api_version]` is the API version, check [supported versions](#supported-api-versions) for the API versions that are currently supported.

`[req_user]` denotes the `user` who is making the request. This is a mandatory attribute that needs to be sent for all APIs in the `params`, unless specified otherwise.


<aside class="notice">
<em>token</em> is mandatory for every API call (except <a href="#signin">Sign In</a>). If this is not provided, an error message will be sent. Refere error section. 
</aside>

# Supported API Versions

Currently these are supported versions of API:

* 1

# Auth

`[req_user]` is not required for APIs under this section.

## Sign In

Attribute | Default | Description
--------- | ------- | -----------
username | None | A unique identifier for every user.
password | None | Required to authenticate a user.

This API checks if the token has expired or not. If expired, new token will be generated and sent with the response.


> Request
>
> POST auth/signin

```json
{
  "username": "username",
  "password": "password"
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Login Successful",
    "data": {
        "id": 12,
        "logged_in": true,
        "username": "username",
        "status": "ACTIVE",
        "personal": {
            "email": "your@email.address",
            "first_name": "First name",
            "last_name": "Last name",
            "full_name": "anurag p",
            "mobile_number": "098XXXXXXX",
            "emergency_contact": "67XXXXXXX1",
            "permanent_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
            "current_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
            "interests": "music, art",
            "linkedin_profile": "https://docs.djangoproject.com/en/1.11/ref/models/fields/#emailfield",
            "location": "Bangalore"
        },
        "business": {
            "company_name": "Company Name",
            "work_email": "work@email.address",
            "contact_number": "098XXXXXXX",
            "location": "Bangalore",
            "employee_id": "unique_employee_id",
            "designation": "Department Head",
            "department": "Mechanical",
            "blood_group": "O+ve",
            "date_of_joining": "2015-07-11",
            "availability": true,
            "linkedin_profile": "https://url/to/linkedin/profile/"
        },
        "token": {
            "token": "AveEEeeeEeeeEEeEEeEEERYLoOOoOOoOONnnNNnNnNnGGGgAcEssToKEn",
            "expires_at": 1532616566
        },
        "role": {},
        "perms": {}
    }
}
```

## Sign Out

Attribute | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user signing out.

> Request
>
> PUT user/[user_id]/signout

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "data": {},
    "message": "Logout Successful"
}
```

## Reset Password

Attribute | Default | Description
--------- | ------- | -----------
username | None | A unique identifier for every user.
old_password | None | Old password.
new_password | None | New password to be set.
re_password | None | New password again to make sure the user is sure of what the they have typed in for password.


> Request
>
> POST auth/signup


```json
{
  "username": "username",
  "old_password": "old_password",
  "new_password": "new_password",
  "re_password": "new_password"
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Password reset Successful. Login to continue"
}
```

## Signup

<aside class="notice">
This API is deprecated, cannot be used.
</aside>

Attribute | Default | Description
--------- | ------- | -----------
username | None | A unique identifier for every user.
password | None | Required to authenticate a user.
re_password | None | Required to make sure the user is sure of what the user has typed in password.
email  | Null | The email address of the user.
mobile_number | Null | The mobile number of the user.

There cannot be duplicate usernames. `username`, `password`, `re_password` are case-sensitive, and are mandatory fields.

As part of response, user details will be provided and a `token` object will be provided. Use the `"token": "AveEEeeeEeeeEEeEEeEEERYLoOOoOOoOONnnNNnNnNnGGGgAcEssToKEn"` for API calls.


> Request
>
> POST auth/signup


```json
{
  "username": "username",
  "password": "password",
  "re_password": "retype password",
  "email": "your@email.address",
  "mobile_number": "098XXXXXXX"
}
```

> Response

```json
{
  "status_code": 200,
  "data": {
      "user": {
          "designation": null,
          "username": "username",
          "full_name": "",
          "id": 1,
          "email": "your@email.address",
          "phone": "098XXXXXXX"
      },
      "token": {
          "expiry": 1529840221,
          "token": "AveEEeeeEeeeEEeEEeEEERYLoOOoOOoOONnnNNnNnNnGGGgAcEssToKEn"
      }
  },
  "message": "Login Successful",
  "status_text": "Success. OK."
}
```