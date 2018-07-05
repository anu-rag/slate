# Group

## Create Group

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | A unique identifier for every user.
name | Null | The name of the group to be kept. Maximum character length 250.
description | Null | The description of the group. Maximum character length 500.
project | Null | Id of the project to which the group will belong to.
members | Null | Array of objects conataining attributes `id`, and `lead`. Ex: [{'id': 19, 'lead': true}, {'id': 20, 'lead': false}]

> Request
>
> POST group/create

```json
{
	"user_id": 15,
	"name": "Department 1",
	"description": "",
	"project": 1,
	"members": [{"id": 23, "lead": false}, {"id": 24, "lead": true}, {"id": 25, "lead": false}]
}
```

> Response

```json
{
    "status_code": 201,
    "status_text": "Created",
    "message": "Group created",
    "group_id": 4
}
```

## Get Group

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.

The `group_id` is an unique integer identifier for a group. 

> Request
>
> GET group/[group_id]?user_id=15

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Members fetched",
    "data": {
        "name": "Test Department",
        "description": "",
        "members": [
            {
                "id": 23,
                "name": "",
                "lead": true
            }
        ]
    }
}
```

## Update Group

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
name | Null | A new name for the group.
description | Null | A new description for the group.
is_active | false | To mark a group as inactive.

Only send the parameter which needs to be updated. For example, to update the group name only send `name` param and its corresponding new value.

The `group_id` is an unique integer identifier for a group. 

> Request
>
> PUT group/[group_id]?user_id=15

```json
{
	"name": "Procurement Department",
	"description": "",
	"is_active": true
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Updated !"
}
```

## Delete Group

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.

The `group_id` is an unique integer identifier for a group. 

> Request
>
> DELETE group/[group_id]?user_id=15

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Group deleted with id: [group_id]"
}
```

## Add Group Members

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
project | Null | Id of the project which the group be associated.
members | Null | Array of objects conataining attributes `id`, and `lead`.

<aside class="notice">
Note: Duplicate members are not supported for one group. A member can be added only once.
</aside>

> Request
>
> POST group/[group_id]/member

```json
{
	"user_id": 15,
	"project": 1,
	"members": [{"id": 23, "lead": false}, {"id": 24, "lead": true}]
}
```

> Response

```json
{
    "status_code": 201,
    "status_text": "Created",
    "message": "Members added"
}
```

## Remove Group Members

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
members | Null | Array of integers(user_ids).

Only if the user_id is part of the group will the user be removed, otherwise not.

> Request
>
> PUT group/[group_id]/member/?user_id=15

```json
{
	"user_id": 15,
	"members": [23, 24]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Members removed from group"
}
```

## Get All Groups

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
project | None | Id of the project for which the groups will be fetched.

<aside class="notice">
Note: Only active groups in a project will be fetched. Only on-going project groups can be fetched.
</aside>

> Request
>
> GET group/list?user_id=15&project=1

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Groups found",
    "data": {
        "groups": [
            {
                "id": 2,
                "name": "Procurement Department",
                "description": "",
                "members": [
                    {
                        "id": 19,
                        "name": "",
                        "lead": true
                    },
                    {
                        "id": 21,
                        "name": "",
                        "lead": false
                    }
                ]
            }
        ]
    }
}
```