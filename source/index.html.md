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
  - task
  - group
  - errors

search: true
---

# Introduction

This is the very first documentation for Taskplus APIs. The request/response format is in json unless specifically mentioned otherwise. Still in development phase, anticipate for changes every now then.

# Making Requests

Since this application is a multi-tenant system, the tenant name is captured in the URL. So, the base URI would be: 
`http://[account_name].shyamasoft.com/api/[api_version]/`. Items inside `[]` are variable. The `[account_name]` is the tenant name and the `[api_version]` is the API version, check [supported versions](#supported-api-versions) for the API versions that are currently supported.

# Supported API Versions

Currently these are supported versions of API:

* 1

# Auth

## Signup

Parameter | Default | Description
--------- | ------- | -----------
username | None | A unique identifier for every user.
password | None | Required to authenticate a user.
re_password | None | Required to make sure the user is sure of what the user has typed in password.
email  | Null | The email address of the user.
mobile_number | Null | The mobile number of the user.

There cannot be duplicate usernames. `username`, `password`, `re_password` are case-sensitive, and are mandatory fields.

As part of response, user details will be provided and a `token` object will be provided. Use the `"token": "AveEEeeeEeeeEEeEEeEEERYLoOOoOOoOONnnNNnNnNnGGGgAcEssToKEn"` for API calls.


<aside class="notice">
Note: this API may be deprecated in favour of user creation from the company itself.
</aside>


<aside class="warning">
<em>token</em> is mandatory for every API call (except <a href="#auth">Auth</a>). If this is not provided, an error message will be sent. Refere error section. 
</aside>

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

## Signin
Parameter | Default | Description
--------- | ------- | -----------
username | None | A unique identifier for every user.
password | None | Required to authenticate a user.

This API checks if the token has expired or not. If expired, new token will be generated and sent with the response.

<aside class="notice">
This API can be used to refresh tokens once they expire.
</aside>


> Request
>
> POST auth/signin

```json
{
  "username": "usernamee",
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
        "token": {
            "token": "AveEEeeeEeeeEEeEEeEEERYLoOOoOOoOONnnNNnNnNnGGGgAcEssToKEn",
            "expiry": 1529506281
        },
        "user": {
            "id": 15,
            "username": "username",
            "full_name": "full_name_of_user",
            "email": "your@email.address",
            "phone": "098XXXXXXX",
            "designation": null
        }
    }
}
```

## Signout
Parameter | Default | Description
--------- | ------- | -----------
username | None | A unique identifier for every user.
password | None | Required to authenticate a user.

> Request
>
> POST auth/signout

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
    "data": {},
    "message": "Logout Successful"
}
```