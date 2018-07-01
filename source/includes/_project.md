# Project

## Create Project

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | A unique identifier for every user.
name | None | The name of the project to be kept. Maximum character length 250.
description | Null | The description of the project. Maximum character length 500.
start_date  | Null | The start date of the project. The start date cannot exceed a year from today's date.
end_date | Null | The end date of the project. The end date cannot exceed a decade from today's date.
members | Null | Array of objects conataining attributes `id`, and `lead`. Ex: [{'id': 19, 'lead': true}, {'id': 20, 'lead': false}]

There will only be `Project Lead`s added during creation of project. No other members can be added with this API.
Other members of the project may be added while creating workgroups(refer [work groups](#supported-api-versions))


<aside class="notice">
Note: The members format maybe changed in future.
</aside>

> Request
>
> POST project/create

```json
{
	"user_id": 15,
	"name": "Test Project",
	"description": "",
	"start_date": "2018-7-01 17:14:7",
	"end_date": "2018-7-10 17:14:7",
	"members": [{"id": 19, "lead": true}, {"id": 23, "lead": false}, {"id": 24, "lead": true}, {"id": 25, "lead": false}, {"id": 19, "lead": false}, {"id": 15, "lead": false}, {"id": 15, "lead": false}]
}
```

> Response

```json
{
    "status_code": 201,
    "status_text": "Created",
    "message": "Project created",
    "data": {
        "project_id": 9
    }
}
```

## Get Project

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | A unique identifier for every user.

The `project_id` is an unique integer identifier for a project. Pass this value to get the corresponding project details
`user_id` is part of query params.
Only open projects can be fetched by this API.


> Request
>
> GET project/[project_id]

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Members fetched",
    "data": {
        "name": "Test Projet Name",
        "description": " ",
        "start_date": "2018-06-01T11:44:07",
        "end_date": "2018-06-10T11:44:07",
        "members": [
            {
                "id": 15,
                "name": "",
                "lead": false
            },
            {
                "id": 19,
                "name": "",
                "lead": false
            },
            {
                "id": 21,
                "name": "",
                "lead": false
            }
        ]
    }
}
```

## Update Project

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | A unique identifier for every user.
name | Null | A new name for the project.
description | Null | A new description for the project.
start_date | Null | Changed start_date, not more than a year from today's date.
end_date | Null | Changed end_date, not more than a decade from today's date.
closed | false | To mark a project as closed.

The `project_id` is an unique integer identifier for a project.

Only send the parameter which needs to be updated. For example, to update the project name only send `name` param and its corresponding new value.

> Request
>
> PUT project/[project_id]

```json
{
	"description": "Test this description",
	"name": "Test Projet Success"
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Updated"
}
```

## Delete Project

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | A unique identifier for every user.

The `project_id` is an unique integer identifier for a project. 
`user_id` is part of query params.

> Request
>
> DELETE project/[project_id]

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Deleted project with id: [project_id]"
}
```

## Add Members

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | A unique identifier for every user.
members | None | Array of objects conataining attributes `id`, and `lead`.

<aside class="notice">
Note: Duplicate members are not supported for one project. A member can be added only once.
</aside>

> Request
>
> POST project/[project_id]/member

```json
{
	"user_id": 15,
	"members": [{"id": 20, "lead": false}]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Members added to project"
}
```

## Remove Members

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | A unique identifier for every user.
members | None | Array of integers(user_ids).

Only if the user_id is part of the project will the user be removed, otherwise not.

> Request
>
> PUT project/[project_id]/member

```json
{
	"user_id": 15,
	"members": [15, 19, 23]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Members removed from project"
}
```

## Get All Projects

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | A unique identifier for every user.

Get all projects related to a user (either created by or assigned to).

> Request
>
> GET project/all

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Projects found",
    "data": {
        "projects": [
            {
                "id": 1,
                "description": " ",
                "name": "Test Projet Name",
                "start_date": "2018-06-01T11:44:07",
                "end_date": "2018-06-10T11:44:07",
                "created_by": 28,
                "members": [
                    {
                        "id": 15,
                        "name": "",
                        "lead": false
                    },
                    {
                        "id": 19,
                        "name": "",
                        "lead": false
                    },
                    {
                        "id": 21,
                        "name": "",
                        "lead": false
                    }
                ]
            },
            {
                "id": 7,
                "description": "",
                "name": "Test Project 5",
                "start_date": "2018-07-01T17:14:07",
                "end_date": "2018-07-10T17:14:07",
                "created_by": 15,
                "members": [
                    {
                        "id": 20,
                        "name": "",
                        "lead": false
                    },
                    {
                        "id": 24,
                        "name": "",
                        "lead": true
                    },
                    {
                        "id": 25,
                        "name": "",
                        "lead": false
                    }
                ]
            }
        ]
    }
}
```