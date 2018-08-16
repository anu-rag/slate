# Task

## Create Task

Attribute   | Default | Description
----------- | ------- | -----------
name        | None    | The name of the project to be kept. Maximum character length 250.
description | Null    | The description of the project. Maximum character length 500.
start_date  | Null    | The start date of the project. The start date cannot exceed a year from today's date.
end_date    | Null    | The end date of the project. The end date cannot exceed a decade from today's date.
assignee    | None    | Id of the user to whom the task will be asigned.
project     | None    | Id of the project to which the task belongs to.
group       | None    | Id of workgroup to which will this task be tied to.
priority    | False   | Set the priority of the task.

A task can be attached to a `project`, `group` has to be in the `project`, and `assignee` should be in that group.
If any of the above fails, task won't be created.
`start_date`, and `end_date` cannot be greater than the project's date range.

<aside class="notice">
By default the <code>assigner</code> of the project will be set as the user who creates a task.
</aside>

> Request
>
> POST task/create

```json
{
    "name": "Test Task",
    "description": "",
    "start_date": "2018-7-02 17:14:7",
    "end_date": "2019-6-01 17:14:7",
    "project": 2,
    "assignee": 5,
    "group": 1,
    "priority": true
}
```

> Response

```json
{
    "status_code": 201,
    "status_text": "Created",
    "message": "Task created",
    "data": {
        "id": 1,
        "creation_date": "2018-07-17T16:58:46.001",
        "name": "Test Task",
        "description": "",
        "start_date": "2018-06-01T17:14:07",
        "end_date": "2018-06-10T17:14:07",
        "status": null,
        "priority": true,
        "assigner": {
            "info": "assigner personal business info"
        },
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
        "assignee": {
            "info": "assignee personal business info"
        },
        "group": {
            "id": 1,
            "creation_date": "2018-07-16T18:16:13",
            "name": "Procurement Department",
            "description": "",
            "status": "ACTIVE"
        }
    }
}
```


## Get Task

Parameter | Default | Description
--------- | ------- | -----------
task_id   | None    | Id of task

Only open tasks can be fetched by this API.

> Request
>
> GET task/[task_id]/

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
        "creation_date": "2018-07-17T20:25:12",
        "name": "Test Task",
        "description": "",
        "start_date": "2018-07-02T17:14:07",
        "end_date": "2019-06-01T17:14:07",
        "status": null,
        "priority": false,
        "assigner": {
            "info": "assigner's personal business info"
        },
        "project": {
            "id": 3,
            "creation_date": "2018-07-14T14:31:50",
            "name": "Project 3",
            "description": "",
            "start_date": "2018-05-10T17:14:07",
            "end_date": "2021-07-01T17:14:07",
            "creator": {
                "info": "creator personal business info"
            },
            "status": null
        },
        "assignee": {
            "info": "assignee personal business info"
        },
        "group": {
            "id": 3,
            "creation_date": "2018-07-17T20:02:23",
            "name": "Department 1",
            "description": "",
            "status": "ACTIVE"
        },
        "followers": [
            {
                "id": 7,
                "logged_in": true,
                "username": "username",
                "status": "ACTIVE",
                "personal": {
                    "email": "your@email.address",
                    "first_name": "first_name",
                    "last_name": "last_name",
                    "full_name": "first_name last_name",
                    "mobile_number": "89XXXXXXX2",
                    "emergency_contact": "67XXXXXX61",
                    "permanent_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
                    "current_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
                    "interests": "music, art"
                },
                "business": {
                    "company_name": null,
                    "work_email": "work@email.address",
                    "contact_number": "9XXXXXX31",
                    "loaction": "Bangalore",
                    "employee_id": "unique_id",
                    "designation": "Department Head",
                    "department": "Mechanical",
                    "blood_group": "O+ve",
                    "date_of_joining": "2015-07-11",
                    "linkedin_profile": "https://url/to/linkedin/profile/"
                }
            }
        ],
        "attachments": [
            {
                "id": 1,
                "url": "/url/to/attachment",
                "added_by": {
                    "id": 2,
                    "logged_in": true,
                    "username": "username",
                    "status": "ACTIVE",
                    "personal": {
                        "email": "your@email.address",
                        "first_name": "first_name",
                        "last_name": "last_name",
                        "full_name": "first_name last_name",
                        "mobile_number": "89XXXXXXX2",
                        "emergency_contact": "67XXXXXX61",
                        "permanent_address": "4th floor, Plot no. 49, Sector 44, Gurugram - 122002, Haryana",
                        "current_address": "4th floor, Plot no. 49, Sector 44, Gurugram - 122002, Haryana",
                        "interests": "music, art",
                        "linkedin_profile": null,
                        "location": "Gurugram"
                    },
                    "business": {
                        "company_name": null,
                        "work_email": "work@email.address",
                        "contact_number": "9XXXXXX31",
                        "loaction": "Bangalore",
                        "employee_id": "unique_id",
                        "department": "Business Development",
                        "blood_group": "O+ve",
                        "date_of_joining": null,
                        "availability": true,
                        "linkedin_profile": null
                    }
                }
            }
        ]
    }
}
```

## Update Task

Attribute   | Default | Description
----------- | ------- | -----------
task_id     | None    | Id of task
name        | Null    | A new name for the task.
description | Null    | A new description for the task.
start_date  | Null    | Changed start_date, not more than a year from today's date.
end_date    | Null    | Changed end_date, not more than a decade from today's date.
assignee    | Null    | New Id of the user whom the task will be assigned to.
group       | Null    | New Id of the workgroup, the task will be part of.

`group` has to be in the project, and `assignee` should be in that group.
If any of the above fails, task won't be updated.
Only send the parameter which needs to be updated. For example, to update the task name only send `name` param and its corresponding new value.

> Request
>
> PUT task/[task_id]/

```json
{
    "name": "Test task 2",
    "assignee": 3
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Updated !",
    "data": {
        "id": 2,
        "creation_date": "2018-07-17T17:06:15",
        "name": "Test task 2",
        "description": "",
        "start_date": "2018-07-02T17:14:07",
        "end_date": "2020-06-01T17:14:07",
        "status": null,
        "priority": false,
        "assigner": {
            "info": "assigner personal business info"
        },
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
        "assignee": {
            "info": "assignee personal business info"
        },
        "group": {
            "id": 1,
            "creation_date": "2018-07-16T18:16:13",
            "name": "Procurement Department",
            "description": "",
            "status": "ACTIVE"
        }
    }
}
```

## Delete Task

Attribute | Default | Description
--------- | ------- | -----------
task_id   | None    | Id of task

> Request
>
> DELETE task/[task_id]/

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Task deleted with id: 6",
    "data": {
        "id": 6,
        "creation_date": "2018-07-17T20:28:04",
        "name": "Test Task",
        "description": "",
        "start_date": "2018-07-02T17:14:07",
        "end_date": "2019-06-01T17:14:07",
        "status": null,
        "priority": true,
        "assigner": {
             "info": "assigner personal business info"
        },
        "project": {
            "id": 3,
            "creation_date": "2018-07-14T14:31:50",
            "name": "Project 3",
            "description": "",
            "start_date": "2018-05-10T17:14:07",
            "end_date": "2021-07-01T17:14:07",
            "creator": {
                 "info": "creator personal business info"
            },
            "status": null
        },
        "assignee": {
             "info": "assignee personal business info"
        },
        "group": {
            "id": 3,
            "creation_date": "2018-07-17T20:02:23",
            "name": "Department 1",
            "description": "",
            "status": "ACTIVE"
        }
    }
}
```

## Delete Tasks

Delete multiple tasks

Attribute | Default | Description
--------- | ------- | -----------
tasks     | None    | Array of integers(task_ids). Maximum length 20.

> Request
>
> PUT task/action/delete

```json
{
    "tasks": [3, 4]
}
```

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Task(s) deleted !",
    "data": {
        "data-list": [
            {
                "id": 3,
                "creation_date": "2018-07-17T20:03:17",
                "name": "Test task 3",
                "description": "",
                "start_date": "2018-07-02T17:14:07",
                "end_date": "2019-06-01T17:14:07",
                "status": null,
                "priority": false,
                "assigner": {
                    "info": "assigner personal business info"
                },
                "project": {
                    "id": 3,
                    "creation_date": "2018-07-14T14:31:50",
                    "name": "Project 3",
                    "description": "",
                    "start_date": "2018-05-10T17:14:07",
                    "end_date": "2021-07-01T17:14:07",
                    "creator": {
                        "info": "creator personal business info"
                    },
                    "status": null
                },
                "assignee": {
                    "info": "assignee personal business info"
                },
                "group": {
                    "id": 3,
                    "creation_date": "2018-07-17T20:02:23",
                    "name": "Department 1",
                    "description": "",
                    "project": {
                        "id": 3,
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
                    "status": "ACTIVE"
                }
            },
            {
                "id": 4,
                "creation_date": "2018-07-17T20:05:35",
                "name": "Test Task",
                "description": "",
                "start_date": "2018-07-02T17:14:07",
                "end_date": "2019-06-01T17:14:07",
                "status": null,
                "priority": false,
                "assigner": {
                    "info": "assigner personal business info"
                },
                "project": {
                    "id": 3,
                    "creation_date": "2018-07-14T14:31:50",
                    "name": "Project 3",
                    "description": "",
                    "start_date": "2018-05-10T17:14:07",
                    "end_date": "2021-07-01T17:14:07",
                    "creator": {
                        "info": "creator personal business info"
                    },
                    "status": null
                },
                "assignee": {
                    "info": "assignee personal business info"
                },
                "group": {
                    "id": 3,
                    "creation_date": "2018-07-17T20:02:23",
                    "name": "Department 1",
                    "description": "",
                    "project": {
                        "id": 3,
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
                    "status": "ACTIVE"
                }
            }
        ]
    }
}
```

## Get All Tasks

Attribute | Default  | Description
--------- | -------- | -----------
status    | ON_GOING | Status of the task
cat       | 11       | Category of the task
filter_by | 3        | Filter for task
fromId    | 1        | Start range
toId      | 20       | End range


User with `View all tasks` permission(admin) can see all tasks in the organisation else
others will see only tasks they are involved in(either as assignee or assigner).
Filters, cat won't be applicable for user with `View all tasks` permission(admin).

Folowing statuses are available:

* ON_GOING - Currently active tasks
* COMPLETED - All tasks marked as complete
* OVERDUE - All tasks past their `end_date`

Following categories are available:

* 11 - all tasks where the assigner is the requesting user
* 12 - all tasks where the assignee is the requesting user
* 13 - all tasks where the requesting user is a follower

Following filters are available:

* 1 - for all tasks that are read by the assignee
* 2 - for all tasks that are unread by the assignee
* 3 - all task sorted by newest (based onn start_date of the tasks)
* 4 - all task sorted by oldest (based onn start_date of the tasks)

Attributes must be provided as params.
Range between `fromId` and `toId` cannot be greater than 20.

<aside class="notice">
Note: Pinned task will always be on top of task list(sorted by newest start_date) irrespective of any status, cat, filter_by
</aside>

> Request
>
> GET task/list

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Tasks found",
    "data": {
        "on_going": 4,
        "complete": 0,
        "over_due": 0,
        "tasks": [
            {
                "id": 2,
                "creation_date": "2018-07-17T17:06:15",
                "name": "Test task 2",
                "description": "",
                "start_date": "2018-07-02T17:14:07",
                "end_date": "2020-06-01T17:14:07",
                "status": null,
                "priority": false,
                "assigner": {
                     "info": "assigner personal business info"
                },
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
                "assignee": {
                     "info": "assignee personal business info"
                },
                "group": {
                    "id": 1,
                    "creation_date": "2018-07-16T18:16:13",
                    "name": "Procurement Department",
                    "description": "",
                    "project": {
                        "id": 3,
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
                    "status": "ACTIVE"
                },
                "pinned": false,
                "followers": [],
                "has_attachment": true
            },
            {
                "id": 3,
                "creation_date": "2018-07-17T20:03:17",
                "name": "Test task 3",
                "description": "",
                "start_date": "2018-07-02T17:14:07",
                "end_date": "2019-06-01T17:14:07",
                "status": null,
                "priority": false,
                "assigner": {
                     "info": "assigner personal business info"
                },
                "project": {
                    "id": 3,
                    "creation_date": "2018-07-14T14:31:50",
                    "name": "Project 3",
                    "description": "",
                    "start_date": "2018-05-10T17:14:07",
                    "end_date": "2021-07-01T17:14:07",
                    "creator": {
                         "info": "creator personal business info"
                    },
                    "status": null
                },
                "assignee": {
                     "info": "assignee personal business info"
                },
                "group": {
                    "id": 3,
                    "creation_date": "2018-07-17T20:02:23",
                    "name": "Department 1",
                    "description": "",
                    "project": {
                        "id": 3,
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
                    "status": "ACTIVE"
                },
                "pinned": false,
                "followers": [],
                "has_attachment": true
            },
            {
                "id": 4,
                "creation_date": "2018-07-17T20:05:35",
                "name": "Test Task",
                "description": "",
                "start_date": "2018-07-02T17:14:07",
                "end_date": "2019-06-01T17:14:07",
                "status": null,
                "priority": true,
                "assigner": {
                     "info": "assigner personal business info"
                },
                "project": {
                    "id": 3,
                    "creation_date": "2018-07-14T14:31:50",
                    "name": "Project 3",
                    "description": "",
                    "start_date": "2018-05-10T17:14:07",
                    "end_date": "2021-07-01T17:14:07",
                    "creator": {
                         "info": "creator personal business info"
                    },
                    "status": null
                },
                "assignee": {
                     "info": "assignee personal business info"
                },
                "group": {
                    "id": 3,
                    "creation_date": "2018-07-17T20:02:23",
                    "name": "Department 1",
                    "description": "",
                    "project": {
                        "id": 3,
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
                    "status": "ACTIVE"
                },
                "pinned": false,
                "followers": [],
                "has_attachment": true
            },
            {
                "id": 5,
                "creation_date": "2018-07-17T20:25:12",
                "name": "Test Task",
                "description": "",
                "start_date": "2018-07-02T17:14:07",
                "end_date": "2019-06-01T17:14:07",
                "status": null,
                "priority": false,
                "assigner": {
                     "info": "assigner personal business info"
                },
                "project": {
                    "id": 3,
                    "creation_date": "2018-07-14T14:31:50",
                    "name": "Project 3",
                    "description": "",
                    "start_date": "2018-05-10T17:14:07",
                    "end_date": "2021-07-01T17:14:07",
                    "creator": {
                         "info": "creator personal business info"
                    },
                    "status": null
                },
                "assignee": {
                     "info": "assignee personal business info"
                },
                "group": {
                    "id": 3,
                    "creation_date": "2018-07-17T20:02:23",
                    "name": "Department 1",
                    "description": "",
                    "project": {
                        "id": 3,
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
                    "status": "ACTIVE"
                },
                "pinned": false,
                "followers": [],
                "has_attachment": true
            }
        ]
    }
}
```

## Get All Followers

This API can be used to fetch all users who can follow any task.

> Request
>
> GET task/follower

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Follower(s) fetched !",
    "data": {
        "data_list": [
            {
                "id": 2,
                "logged_in": true,
                "username": "username",
                "status": "ACTIVE",
                "personal": {
                    "email": "your@email.address",
                    "first_name": "first_name",
                    "last_name": "last_name",
                    "full_name": "first_name last_name",
                    "mobile_number": "89XXXXXXX2",
                    "emergency_contact": "67XXXXXX61",
                    "permanent_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
                    "current_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
                    "interests": "music, art"
                },
                "business": {
                    "company_name": null,
                    "work_email": "work@email.address",
                    "contact_number": "9XXXXXX31",
                    "loaction": "Bangalore",
                    "employee_id": "unique_id",
                    "designation": "Department Head",
                    "department": "Mechanical",
                    "blood_group": "O+ve",
                    "date_of_joining": "2015-07-11",
                    "linkedin_profile": "https://url/to/linkedin/profile/"
                }
            }
        ]
    }
}
```

## Add Followers to a task

Attribute | Default  | Description
--------- | -------- | -----------
task_id   | None     | Id of the task
followers | None     | Array of integers(user_ids). Maximum length 20.

<aside class="notice">
Note: Only users who have permission to follow tasks will be added as follower for a task. Rest will be ignored.
</aside>


> Request
>
> POST task/follower

```json
{
    "task_id": 5,
    "followers": [2, 5]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Follower(s) added !",
    "data": {
        "data_list": [
            {
                "id": 2,
                "logged_in": true,
                "username": "username",
                "status": "ACTIVE",
                "personal": {
                    "email": "your@email.address",
                    "first_name": "first_name",
                    "last_name": "last_name",
                    "full_name": "first_name last_name",
                    "mobile_number": "89XXXXXXX2",
                    "emergency_contact": "67XXXXXX61",
                    "permanent_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
                    "current_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
                    "interests": "music, art"
                },
                "business": {
                    "company_name": null,
                    "work_email": "work@email.address",
                    "contact_number": "9XXXXXX31",
                    "loaction": "Bangalore",
                    "employee_id": "unique_id",
                    "designation": "Department Head",
                    "department": "Mechanical",
                    "blood_group": "O+ve",
                    "date_of_joining": "2015-07-11",
                    "linkedin_profile": "https://url/to/linkedin/profile/"
                }
            }
        ]
    }
}
```


## Remove Followers from a task

Attribute | Default  | Description
--------- | -------- | -----------
task_id   | None     | Id of the task
followers | None     | Array of integers(user_ids). Maximum length 20.


> Request
>
> PUT task/follower

```json
{
    "task_id": 5,
    "followers": [2]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Follower(s) removed !",
    "data": {
        "data_list": [
            {
                "id": 2,
                "logged_in": true,
                "username": "username",
                "status": "ACTIVE",
                "personal": {
                    "email": "your@email.address",
                    "first_name": "first_name",
                    "last_name": "last_name",
                    "full_name": "first_name last_name",
                    "mobile_number": "89XXXXXXX2",
                    "emergency_contact": "67XXXXXX61",
                    "permanent_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
                    "current_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
                    "interests": "music, art"
                },
                "business": {
                    "company_name": null,
                    "work_email": "work@email.address",
                    "contact_number": "9XXXXXX31",
                    "loaction": "Bangalore",
                    "employee_id": "unique_id",
                    "designation": "Department Head",
                    "department": "Mechanical",
                    "blood_group": "O+ve",
                    "date_of_joining": "2015-07-11",
                    "linkedin_profile": "https://url/to/linkedin/profile/"
                }
            }
        ]
    }
}
```

## Mark tasks as favourite

Attribute | Default  | Description
--------- | -------- | -----------
tasks     | None     | Array of integers(task_ids). Maximum length 20.


> Request
>
> POST task/action/favourite

```json
{
    "tasks": [3]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Favourites added !",
    "data": {
        "user": {
            "id": 2,
            "logged_in": true,
            "username": "username",
            "status": "ACTIVE",
            "personal": {
                "email": "your@email.address",
                "first_name": "first_name",
                "last_name": "last_name",
                "full_name": "first_name last_name",
                "mobile_number": "89XXXXXXX2",
                "emergency_contact": "67XXXXXX61",
                "permanent_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
                "current_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
                "interests": "music, art"
            },
            "business": {
                "company_name": null,
                "work_email": "work@email.address",
                "contact_number": "9XXXXXX31",
                "loaction": "Bangalore",
                "employee_id": "unique_id",
                "designation": "Department Head",
                "department": "Mechanical",
                "blood_group": "O+ve",
                "date_of_joining": "2015-07-11",
                "linkedin_profile": "https://url/to/linkedin/profile/"
            }
        },
        "tasks": [
            {
                "id": 2,
                "creation_date": "2018-07-17T17:06:15",
                "name": "Test task 2",
                "description": "",
                "start_date": "2018-07-02T17:14:07",
                "end_date": "2020-06-01T17:14:07",
                "status": null,
                "priority": false,
                "assigner": {
                    "info": "assigner personal business info"
                },
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
                "assignee": {
                    "info": "assignee personal business info"
                },
                "group": {
                    "id": 3,
                    "creation_date": "2018-07-17T20:02:23",
                    "name": "Department 1",
                    "description": "",
                    "status": null
                }
            }
        ]
    }
}
```

## Remove tasks from favourites

Attribute | Default  | Description
--------- | -------- | -----------
tasks     | None     | Array of integers(task_ids). Maximum length 20.


> Request
>
> PUT task/action/unfavourite

```json
{
    "tasks": [3]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Favourites removed !"
}
```

## Mark tasks as read

Attribute | Default  | Description
--------- | -------- | -----------
tasks     | None     | Array of integers(task_ids). Maximum length 20.


<aside class="notice">
Note: Only an assignee can mark task as read. This is stored at a task level.
</aside>

> Request
>
> PUT task/action/read

```json
{
    "tasks": [3]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Task marked as read !"
}
```

## Deprioritize Tasks

Attribute | Default  | Description
--------- | -------- | -----------
tasks     | None     | Array of integers(task_ids). Maximum length 20.


> Request
>
> PUT task/action/deprioritize

```json
{
    "tasks": [3]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Task(s) deprioritized !"
}
```

## Mark tasks as complete

Attribute | Default  | Description
--------- | -------- | -----------
tasks     | None     | Array of integers(task_ids). Maximum length 20.

<aside class="notice">
Note: Only an assignee can mark task as complete.
</aside>


> Request
>
> PUT task/action/complete

```json
{
    "tasks": [3]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Task marked as complete !",
    "data": [
        {
            "id": 7,
            "creation_date": "2018-07-19T22:30:46",
            "name": "Test task 2",
            "description": "",
            "start_date": "2018-07-02T17:14:07",
            "end_date": "2019-06-01T17:14:07",
            "status": "COMPLETED",
            "priority": true,
            "assigner": {
                "info": "assigner personal business info"
            },
            "project": {
                "id": 3,
                "creation_date": "2018-07-14T14:31:50",
                "name": "Project 3",
                "description": "",
                "start_date": "2018-05-10T17:14:07",
                "end_date": "2021-07-01T17:14:07",
                "creator": {
                    "info": "creator personal business info"
                },
                "status": null
            },
            "assignee": {
                "info": "assignee personal business info"
            },
            "group": {
                "id": 3,
                "creation_date": "2018-07-17T20:02:23",
                "name": "Department 1",
                "description": "",
                "status": null
            }
        }
    ]
}
```

## Reopen Tasks

Attribute | Default  | Description
--------- | -------- | -----------
tasks     | None     | Array of integers(task_ids). Maximum length 20.

<aside class="notice">
Note: Only an assigner can reopen a task. Only <em>completed</em> tasks can be reopened.
</aside>


> Request
>
> PUT task/action/reopen

```json
{
    "tasks": [3]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Task(s) reopened !",
    "data": [
        {
            "id": 3,
            "creation_date": "2018-07-17T20:25:12",
            "name": "Test Task",
            "description": "",
            "start_date": "2018-07-05T17:14:07",
            "end_date": "2019-06-01T17:14:07",
            "status": "REOPEN",
            "read": true,
            "priority": false,
            "assigner": {
                "info": "assigner personal business info"
            },
            "project": {
                "id": 3,
                "creation_date": "2018-07-14T14:31:50",
                "name": "Project 3",
                "description": "",
                "start_date": "2018-05-10T17:14:07",
                "end_date": "2021-07-01T17:14:07",
                "creator": {
                    "info": "creator personal business info"
                },
                "status": null
            },
            "assignee": {
                "info": "assignee personal business info"
            },
            "group": {
                "id": 3,
                "creation_date": "2018-07-17T20:02:23",
                "name": "Department 1",
                "description": "",
                "status": null
            }
        }
    ]
}
```

## Close Tasks

Attribute | Default  | Description
--------- | -------- | -----------
tasks     | None     | Array of integers(task_ids). Maximum length 20.

<aside class="notice">
Note: Only assigners can mark task as closed.
</aside>


> Request
>
> PUT task/action/close

```json
{
    "tasks": [7]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Task marked as complete !",
    "data": [
        {
            "id": 7,
            "creation_date": "2018-07-19T22:30:46",
            "name": "Test task 2",
            "description": "",
            "start_date": "2018-07-02T17:14:07",
            "end_date": "2019-06-01T17:14:07",
            "status": "CLOSED",
            "priority": true,
            "assigner": {
                "info": "assigner personal business info"
            },
            "project": {
                "id": 3,
                "creation_date": "2018-07-14T14:31:50",
                "name": "Project 3",
                "description": "",
                "start_date": "2018-05-10T17:14:07",
                "end_date": "2021-07-01T17:14:07",
                "creator": {
                    "info": "creator personal business info"
                },
                "status": null
            },
            "assignee": {
                "info": "assignee personal business info"
            },
            "group": {
                "id": 3,
                "creation_date": "2018-07-17T20:02:23",
                "name": "Department 1",
                "description": "",
                "status": "ACTIVE"
            }
        }
    ]
}
```

# Task Comment

## Add Comment

Attribute | Default | Description
--------- | ------- | -----------
task_id   | None    | Id of the task
comment   | Null    | Comment to add to a task. Maximum character length 1000.


> Request
>
> POST task/[task_id]/comment

```json
{
	"comment": "Yay! Now I can add comments"
}
```

> Response

```json
{
    "status_code": 201,
    "status_text": "Created",
    "message": "Comment added",
    "data": {
        "id": 1,
        "comment": "Yay! Now I can add comments",
        "commentor": {
            "id": 2,
            "logged_in": true,
            "username": "username",
            "status": "ACTIVE",
            "personal": {
                "email": "your@email.address",
                "first_name": "first_name",
                "last_name": "last_name",
                "full_name": "first_name last_name",
                "mobile_number": "89XXXXXXX2",
                "emergency_contact": "67XXXXXX61",
                "permanent_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
                "current_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
                "interests": "music, art"
            },
            "business": {
                "company_name": null,
                "work_email": "work@email.address",
                "contact_number": "9XXXXXX31",
                "loaction": "Bangalore",
                "employee_id": "unique_id",
                "designation": "Department Head",
                "department": "Mechanical",
                "blood_group": "O+ve",
                "date_of_joining": "2015-07-11",
                "linkedin_profile": "https://url/to/linkedin/profile/"
            }
        },
        "task": {
            "id": 1,
            "creation_date": "2018-07-17T16:58:46",
            "name": "Test Task",
            "description": "",
            "start_date": "2018-06-01T17:14:07",
            "end_date": "2018-06-10T17:14:07",
            "status": null,
            "priority": false,
            "assigner": {
                "info": "assigner personal business info"
            },
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
            "assignee": {
                "info": "assignee personal business info"
            },
            "group": {
                "id": 3,
                "creation_date": "2018-07-17T20:02:23",
                "name": "Department 1",
                "description": "",
                 "project": {
                    "id": 3,
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
                "status": "ACTIVE"
            }
        }
    }
}
```

## Get Comments

Attribute | Default | Description
--------- | ------- | -----------
task_id   | None    | Id of the task

Get all comments for a task identified by `[task_id]`

> Request
>
> GET task/[task_id]/comment

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Commented fetched",
    "data": {
        "id": 1,
        "creation_date": "2018-07-17T16:58:46",
        "name": "Test Task",
        "description": "",
        "start_date": "2018-06-01T17:14:07",
        "end_date": "2018-06-10T17:14:07",
        "status": null,
        "priority": false,
        "assigner": {
            "info": "assigner personal business info"
        },
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
        "assignee": {
            "info": "assignee personal business info"
        },
        "group": {
            "id": 3,
            "creation_date": "2018-07-17T20:02:23",
            "name": "Department 1",
            "description": "",
            "status": "ACTIVE"
        },
        "comments": [
            {
                "id": 1,
                "comment": "some comment",
                "commentor": {
                    "info": "commentor personal business info"
                }
            }
        ]
    }
}
```

## Update Comment

Attribute  | Default | Description
---------- | ------- | -----------
task_id    | None    | Id of the task
comment_id | None    | Id of the comment to update
comment    | None    | New comment

`comment_id` should be provided as params.

> Request
>
> PUT task/[task_id]/comment?comment_id=[comment_id]

```json
{
    "comment": "new comment"
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Comment Updated !",
    "data": {
        "id": 1,
        "comment": "new comment",
        "commentor": {
            "info": "commentor personal business info"
        },
        "task": {
            "id": 1,
            "creation_date": "2018-07-17T16:58:46",
            "name": "Test Task",
            "description": "",
            "start_date": "2018-06-01T17:14:07",
            "end_date": "2018-06-10T17:14:07",
            "status": null,
            "priority": false,
            "assigner": {
                "info": "assigner personal business info"
            },
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
            "assignee": {
                "info": "assignee personal business info"
            },
            "group": {
                "id": 3,
                "creation_date": "2018-07-17T20:02:23",
                "name": "Department 1",
                "description": "",
                 "project": {
                    "id": 3,
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
                "status": "ACTIVE"
            }
        }
    }
}
```

## Delete Comment(s)

Attribute  | Default | Description
---------- | ------- | -----------
task_id    | None    | Id of the task
comment_id | None    | Id of the comment to delete

This API can used to delete one comment, and all comments for a given task by `task_id`.
If `comment_id` is provided then that specific comment will be deleted, else all comments will be deleted.
`comment_id` should be provided as params.

> Request
>
> DELETE task/[task_id]/comment?comment_id=[comment_id]

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Comment(s) deleted"
}
```

# Task Checklist

## Add Checklist

Attribute  | Default | Description
---------- | ------- | -----------
task_id    | None    | Id of the task
check_list | None    | Array of strings or integers.


> Request
>
> POST task/[task_id]/check_list

```json
{
	"check_list": ["a", "b"]
}
```

> Response

```json
{
    "status_code": 201,
    "status_text": "Created",
    "message": "Check list created",
    "data": {
        "id": 1,
        "creation_date": "2018-07-17T16:58:46",
        "name": "Test Task",
        "description": "",
        "start_date": "2018-06-01T17:14:07",
        "end_date": "2018-06-10T17:14:07",
        "status": null,
        "read": false,
        "priority": false,
        "assigner": {
            "info": "assigner personal business info"
        },
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
        "assignee": {
            "info": "assignee personal business info"
        },
        "group": {
            "id": 3,
            "creation_date": "2018-07-17T20:02:23",
            "name": "Department 1",
            "description": "",
             "project": {
                "id": 3,
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
            "status": "ACTIVE"
        },
        "check_list": [
            {
                "id": 23,
                "item": "a",
                "checked": false
            },
            {
                "id": 24,
                "item": "b",
                "checked": false
            }
        ]
    }
}
```

## Get Checklist

Attribute  | Default | Description
---------- | ------- | -----------
task_id    | None    | Id of the task


> Request
>
> GET task/[task_id]/check_list

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Check list fetched",
    "data": {
        "id": 3,
        "creation_date": "2018-07-17T20:03:17",
        "name": "Test task 3",
        "description": "",
        "start_date": "2018-07-02T17:14:07",
        "end_date": "2019-06-01T17:14:07",
        "status": null,
        "priority": false,
        "assigner": {
            "info": "assigner personal business info"
        },
        "project": {
            "id": 3,
            "creation_date": "2018-07-14T14:31:50",
            "name": "Project 3",
            "description": "",
            "start_date": "2018-05-10T17:14:07",
            "end_date": "2021-07-01T17:14:07",
            "creator": {
                "info": "creator personal business info"
            },
            "status": null
        },
        "assignee": {
            "info": "assignee personal business info"
        },
        "group": {
            "id": 3,
            "creation_date": "2018-07-17T20:02:23",
            "name": "Department 1",
            "description": "",
            "status": "ACTIVE"
        },
        "check_list": [
            {
                "id": 1,
                "item": "a",
                "checked": true
            },
            {
                "id": 2,
                "item": "b",
                "checked": false
            },
            {
                "id": 3,
                "item": "a",
                "checked": false
            },
            {
                "id": 4,
                "item": "b",
                "checked": false
            },
            {
                "id": 5,
                "item": "a",
                "checked": false
            },
            {
                "id": 6,
                "item": "b",
                "checked": false
            },
            {
                "id": 7,
                "item": "a",
                "checked": false
            },
            {
                "id": 8,
                "item": "b",
                "checked": false
            },
            {
                "id": 9,
                "item": "a",
                "checked": false
            },
            {
                "id": 10,
                "item": "b",
                "checked": false
            },
            {
                "id": 11,
                "item": "a",
                "checked": false
            },
            {
                "id": 12,
                "item": "b",
                "checked": false
            },
            {
                "id": 13,
                "item": "a",
                "checked": false
            },
            {
                "id": 14,
                "item": "b",
                "checked": false
            },
            {
                "id": 15,
                "item": "a",
                "checked": false
            },
            {
                "id": 16,
                "item": "b",
                "checked": false
            }
        ]
    }
}
```

## Update Checklist

Attribute  | Default | Description
---------- | ------- | -----------
task_id    | None    | Id of the task
check_list | None    | Array of objects

This API can be used to update the checklist item by item, also to mark item as checked(in case of done).

> Request
>
> PUT task/[task_id]/check_list

```json
{
    "check_list": [{"id": 21, "check_item": "a", "checked": true}]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Check list Updated",
    "data": {
        "id": 3,
        "creation_date": "2018-07-17T20:03:17",
        "name": "Test task 3",
        "description": "",
        "start_date": "2018-07-02T17:14:07",
        "end_date": "2019-06-01T17:14:07",
        "status": null,
        "priority": false,
        "assigner": {
            "info": "assigner personal business info"
        },
        "project": {
            "id": 3,
            "creation_date": "2018-07-14T14:31:50",
            "name": "Project 3",
            "description": "",
            "start_date": "2018-05-10T17:14:07",
            "end_date": "2021-07-01T17:14:07",
            "creator": {
                "info": "creator personal business info"
            },
            "status": null
        },
        "assignee": {
            "info": "assignee personal business info"
        },
        "group": {
            "id": 3,
            "creation_date": "2018-07-17T20:02:23",
            "name": "Department 1",
            "description": "",
            "status": "ACTIVE"
        },
        "check_list": [
            {
                "id": 1,
                "item": "a",
                "checked": true
            }
        ]
    }
}
```

## Delete Checklist

Attribute   | Default | Description
----------- | ------- | -----------
task_id     | None    | Id of the task
checkListId | Null    | Id of the checklist item

This API can used to delete one checklist item, and all checklist items for a given task by `task_id`.
If `checkListId` is provided then that specific item of checklist will be deleted, else all items in checklist will be deleted.
`checkListId` should be provided as params.

> Request
>
> DELETE task/[task_id]/check_list?checkListId=[checkListId]

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Check list item(s) Deleted"
}
```

# Task Attachment

## Upload Attachment

<aside class="warning">
This API accepts only form-data.
</aside>

Attribute   | Default | Description
----------- | ------- | -----------
task_id     | None    | Id of the task
doc         | None    | File(s) to be uploaded.

Supported File Formats:<br>
PDF, JPEG, JPG, PNG, TIFF, DOC, DOCX, PPT, PPS, PPTX, XLS, ZIP, TXT, GIF

<aside class="notice">
Multiple files can be uploaded using this API but the total size should not exceed 5 MB.
</aside>

> Request
>
> POST task/[task_id]/attachment

```json
{
    "doc": "files"
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Document uploaded",
    "data": {
        "data_list": [
            {
                "id": 1,
                "url": "/url/to/attachment",
                "added_by": {
                    "id": 2,
                    "logged_in": true,
                    "username": "username",
                    "status": "ACTIVE",
                    "personal": {
                        "email": "your@email.address",
                        "first_name": "first_name",
                        "last_name": "last_name",
                        "full_name": "first_name last_name",
                        "mobile_number": "89XXXXXXX2",
                        "emergency_contact": "67XXXXXX61",
                        "permanent_address": "4th floor, Plot no. 49, Sector 44, Gurugram - 122002, Haryana",
                        "current_address": "4th floor, Plot no. 49, Sector 44, Gurugram - 122002, Haryana",
                        "interests": "music, art",
                        "linkedin_profile": null,
                        "location": "Gurugram"
                    },
                    "business": {
                        "company_name": null,
                        "work_email": "work@email.address",
                        "contact_number": "9XXXXXX31",
                        "loaction": "Bangalore",
                        "employee_id": "unique_id",
                        "designation": "Director",
                        "department": "Business Development",
                        "blood_group": "O+ve",
                        "date_of_joining": null,
                        "availability": true,
                        "linkedin_profile": null
                    }
                }
            }
        ]
    }
}
```

## Delete Attachment

Attribute   | Default | Description
----------- | ------- | -----------
task_id     | None    | Id of the task
docs_id     | Null    | Id of the document

`docs_id` should be sent as query params.

<aside class="notice">
This API can be used to delete all attachments for a task, and also only one attachment.<br>
If <code>docs_id</code> is given then only that attachment will be deleted.
</aside>

> Request
>
> DELETE task/[task_id]/attachment

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Attachment(s) deleted"
}
```