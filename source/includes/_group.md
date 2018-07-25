# WorkGroup

## Create Group

Attribute | Default | Description
--------- | ------- | -----------
name | Null | The name of the group to be kept. Maximum character length 250.
description | Null | The description of the group. Maximum character length 500.
project | Null | Id of the project to which the group will belong to.

> Request
>
> POST group/create

```json
{
    "name": "Department 1",
    "description": "",
    "project": 2
}
```

> Response

```json
{
    "status_code": 201,
    "status_text": "Created",
    "message": "Group created",
    "data": {
        "id": 1,
        "creation_date": "2018-07-16T18:16:13.787",
        "name": "Department 1",
        "description": "",
        "project": {
            "id": 2,
            "creation_date": "2018-07-14T13:30:12",
            "name": "Project 2",
            "description": "",
            "start_date": "2018-07-01T17:14:07",
            "end_date": "2020-07-01T17:14:07",
            "creator": {
                "info": "creator personal business info"
            },
            "status": null
        },
        "status": null
    }
}
```

## Get Group

Attribute | Default | Description
--------- | ------- | -----------
group_id  | None    | Id of group


> Request
>
> GET group/[group_id]

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Group fetched",
    "data": {
        "id": 5,
        "creation_date": "2018-07-19T22:19:17",
        "name": "Department 2",
        "description": "",
        "project": {
            "id": 2,
            "creation_date": "2018-07-14T13:30:12",
            "name": "Project 2",
            "description": "",
            "start_date": "2018-07-01T17:14:07",
            "end_date": "2020-07-01T17:14:07",
            "creator": {
                "info": "creator personal business info"
            },
            "status": null
        },
        "status": "ACTIVE",
        "members": [],
        "managers": [
            {
                "info": "user's personal business info"
            }
        ]
    }
}
```

## Update Group

Attribute  | Default | Description
---------  | ------- | -----------
group_id   | None    | Id of group
name       | Null    | A new name for the group.
description| Null    | A new description for the group.

Only send the parameter which needs to be updated. For example, to update the group name only send `name` param and its corresponding new value.

> Request
>
> PUT group/[group_id]

```json
{
    "name": "Procurement Department",
    "description": ""
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Updated !",
    "data": {
        "id": 1,
        "creation_date": "2018-07-16T18:16:13",
        "name": "Procurement Department",
        "description": "",
        "project": {
            "id": 2,
            "creation_date": "2018-07-14T13:30:12",
            "name": "Project 2",
            "description": "",
            "start_date": "2018-07-01T17:14:07",
            "end_date": "2020-07-01T17:14:07",
            "creator": {
                "info": "creator personal business info"
            },
            "status": null
        },
        "status": null
    }
}
```

## Delete Group

Attribute | Default | Description
--------- | ------- | -----------
group_id  | None    | Id of group

> Request
>
> DELETE group/[group_id]

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

Attribute | Default | Description
--------- | ------- | -----------
group_id  | None    | Id of group
members   | Null    | Array of objects conataining attributes `id`, and `lead`. Maximum length 20.


<aside class="notice">
Note: Duplicate members are not supported for one group. A member can be added only once.
</aside>

> Request
>
> POST group/[group_id]/member

```json
{
	"members": [{"id": 23, "lead": false}, {"id": 24, "lead": true}]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Members added",
    "data": [
        {
            "info": "user's personal business info",
            "lead": false
        },
        {
            "info": "user's personal business info",
            "lead": true
        }
    ]
}
```

## Remove Group Members

Attribute | Default | Description
--------- | ------- | -----------
group_id  | None    | Id of group
members   | None    | Array of integers(user_ids). Maximum length 20.

Only if the user_id is part of the group will the user be removed, otherwise not.

> Request
>
> PUT group/[group_id]/member/

```json
{
    "members": [3, 4]
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

This API fetches the details of the project, all active groups within this project and only the group leads (project leads)


Attribute | Default | Description
--------- | ------- | -----------
project   | None    | Id of the project for which the groups will be fetched.
fromId    | 1       | Start range
toId      | 20      | End range

Attributes must be provided as params.

<aside class="notice">
Note: Only active groups in a project will be fetched. Only on-going project groups can be fetched.
Note: Range between <code>fromId</code> and <code>toId</code> cannot be greater than 20.
</aside>


> Request
>
> GET group/list

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Groups found",
    "data": {
        "project": {
            "id": 2,
            "creation_date": "2018-07-14T13:30:12",
            "name": "Project 2",
            "description": "",
            "start_date": "2018-07-01T17:14:07",
            "end_date": "2020-07-01T17:14:07",
            "creator": {
                "info": "creator personal business info"
            },
            "status": null
        },
        "managers": [
            {
                "info": "user's personal business info",
            }
        ],
        "groups": [
            {
                "id": 1,
                "creation_date": "2018-07-16T18:16:13",
                "name": "Procurement Department",
                "description": "",
                "status": "ACTIVE",
                "lead": []
            },
            {
                "id": 5,
                "creation_date": "2018-07-19T22:19:17",
                "name": "Department 2",
                "description": "",
                "status": "ACTIVE",
                "lead": [
                    {
                        "info": "user's personal business info",
                        "lead": true
                    }
                ]
            },
            {
                "id": 6,
                "creation_date": "2018-07-23T19:37:04",
                "name": "Procurement Department",
                "description": "",
                "status": null,
                "lead": []
            }
        ]
    }
}
```