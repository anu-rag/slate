# Task

## Create Task

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | A unique identifier for every user.
name | Null | The name of the project to be kept. Maximum character length 250.
description | Null | The description of the project. Maximum character length 500.
start_date  | Null | The start date of the project. The start date cannot exceed a year from today's date.
end_date | Null | The end date of the project. The end date cannot exceed a decade from today's date.
assignee | Null | Id of the user to whom the task will be asigned.
project | Null | Id of the project to which the task belongs to.
group | Null | Id of workgroup to which will this task be tied to.

<aside class="notice">
By default the <code>assigner</code> of the project will be set as the user who creates a task.
</aside>

> Request
>
> POST task/create

```json
{
	"user_id": 34,
	"name": "Test Task 2",
	"description": "",
	"start_date": "2018-6-01 17:14:7",
	"end_date": "2018-6-10 17:14:7",
	"project": 1,
	"assignee": 34,
	"group": 4
}
```

> Response

```json
{
    "status_code": 201,
    "status_text": "Created",
    "message": "Task created",
    "data": {
        "task_id": 1
    }
}
```


## Get Task

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.

The `task_id` is an unique integer identifier for a task. Pass this value to get the corresponding task details.
Only open tasks can be fetched by this API.

> Request
>
> GET task/[task_id]/?user_id=15

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Task fetched",
    "data": {
        "id": 5,
        "name": "Test Task 2",
        "description": "",
        "start_date": "2018-06-01T17:14:07",
        "end_date": "2018-06-10T17:14:07",
        "project": 4,
        "assigned_to": {
            "id": 34,
            "name": ""
        },
        "assigned_by": {
            "id": 34,
            "name": ""
        },
        "group": {
            "id": 5,
            "name": "Department 1"
        }
    }
}
```

## Update Task

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
name | Null | A new name for the task.
description | Null | A new description for the task.
start_date | Null | Changed start_date, not more than a year from today's date.
end_date | Null | Changed end_date, not more than a decade from today's date.
assignee | Null | New Id of the user whom the task will be assigned to.
group | Null | New Id of the workgroup, the task will be part of.
close_task | false | To mark the task as closed.

The `task_id` is an unique integer identifier for a task.

Only send the parameter which needs to be updated. For example, to update the task name only send `name` param and its corresponding new value.

> Request
>
> PUT task/[task_id]/?user_id=15

```json
{
	"name": "Test task 2",
	"description": "",
	"start_date": "",
	"end_date": "",
	"assignee": 15
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

## Delete Task

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.

The `task_id` is an unique integer identifier for a project. 

> Request
>
> DELETE task/[task_id]/?user_id=15

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Task deleted with id: [task_id]"
}
```

## Get All Tasks

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.

Fetches all tasks where the `assignee` or `assigner` is the requesting user.
Correspondingly, the response will contain a boolean value(true / false) in each task object such as `assigned_to_me`, `assigned_by_me` to indicate if the requesting user is an assignee or assigner.


> Request
>
> GET task/list?user_id=15

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Tasks found",
    "data": [
        {
            "id": 6,
            "assigner": {
                "id": 34,
                "name": ""
            },
            "name": "Test task 2",
            "description": "",
            "start_date": "2018-06-01T17:14:07",
            "end_date": "2018-06-10T17:14:07",
            "assignee": {
                "id": 15,
                "name": ""
            },
            "project": {
                "id": 1,
                "name": "Test Projet Name"
            },
            "group": {
                "id": 4,
                "name": "Test Department 1"
            },
            "assigned_to_me": true
        }
    ]
}
```

## Add Comment

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
comment | Null | Comment to add to a task. Maximum character length 1000.


> Request
>
> POST task/[task_id]/comment

```json
{
	"user_id": 15,
	"comment": "Yay! Now I can add comments"
}
```

> Response

```json
{
    "status_code": 201,
    "status_text": "Created",
    "message": "Commented added",
    "data": {
        "comment": "Yay! Now I can add comments",
        "commenter": {
            "id": 15,
            "name": ""
        },
        "task": 1
    }
}
```

## Fetch Comments

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.

Get all comments for a task identified by `[task_id]`

> Request
>
> GET task/[task_id]/comment?user_id=15

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Created",
    "message": "Commented fetched",
    "data": [
        {
            "id": 1,
            "comment": "some\\ comment",
            "added_on": "2018-06-19T19:37:40",
            "task": 4,
            "added_by": {
                "id": 34,
                "name": ""
            }
        },
        {
            "id": 2,
            "comment": "some\\ comment",
            "added_on": "2018-06-19T19:54:19",
            "task": 4,
            "added_by": {
                "id": 34,
                "name": ""
            }
        },
        {
            "id": 3,
            "comment": "some more comment",
            "added_on": "2018-06-19T19:55:04",
            "task": 4,
            "added_by": {
                "id": 34,
                "name": ""
            }
        },
        {
            "id": 4,
            "comment": "some comment",
            "added_on": "2018-06-19T23:10:20",
            "task": 4,
            "added_by": {
                "id": 34,
                "name": ""
            }
        },
        {
            "id": 5,
            "comment": "some comment",
            "added_on": "2018-06-19T23:11:55",
            "task": 4,
            "added_by": {
                "id": 34,
                "name": ""
            }
        }
    ]
}
```

## Add Checklist

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
check_list | None | Array of strings or integers.


> Request
>
> GET task/[task_id]/check_list

```json
{
	"user_id": 34,
	"check_list": ["a", "b"]
}
```

> Response

```json
{
    "status_code": 201,
    "status_text": "Created",
    "message": "Check list created"
}
```