# Project

## Create a project

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