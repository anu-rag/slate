# Notifications

## Get notification count

Attribute  | Default | Description
---------- | ------- | -----------
count      | Null    | true/false


> Request
>
> GET notification/?count=true

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Notifications fetched",
    "data": {
        "count": 5
    }
}
```

## Get notifications

Attribute | Default  | Description
--------- | -------- | -----------
fromId    | 1        | Start range
toId      | 20       | End range


Fetch all notifications pertaining to a user.

Attributes must be provided as params.
Range between `fromId` and `toId` cannot be greater than 20.

> Request
>
> GET notification/

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Notifications fetched",
    "data": {
        "data_list": [
            "user x removed permission(s) to role Admin",
            "user x added members to Sucees Project",
            "user x removed members from Sucees Project",
            "user x marked as complete Sucees Project",
            "user x favourited Project 3",
            "user x created Department 2",
            "user x  Department 2",
            "user x added members to Department 2",
            "user x removed members from Department 2",
            "user x assigned permission(s) to role Admin",
            "user x removed permission(s) to role Admin",
            "user x assigned permission(s) to role Admin",
            "user x removed followers Test Task",
            "user x removed followers Test Task",
            "user x removed followers Test Task",
            "user x removed followers Test Task",
            "user x favourited Sucees Project",
            "user x removed permission(s) to role Admin",
            "user x favourited Project 3",
            "user x assigned permission(s) to role Admin"
        ]
    }
}
```

## Mark all as read

Attribute  | Default | Description
---------- | ------- | -----------
read       | None    | true/false


> Request
>
> PUT notification/

```json
{
	"read": true
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Notifications marked as read"
}
```