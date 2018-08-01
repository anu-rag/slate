# Project

## Create Project

Attribute | Default | Description
--------- | ------- | -----------
name      | None | The name of the project to be kept. Maximum character length 250.
description | Null | The description of the project. Maximum character length 500.
start_date  | Null | The start date of the project. The start date cannot exceed a year from today's date.
end_date  | Null | The end date of the project. The end date cannot exceed a decade from today's date.


> Request
>
> POST project/create

```json
{
	"name": "Test Project",
	"description": "",
	"start_date": "2018-7-01 17:14:7",
	"end_date": "2018-7-10 17:14:7"
}
```

> Response

```json
{
    "status_code": 201,
    "status_text": "Created",
    "message": "Project created",
    "data": {
        "id": 1,
        "creation_date": "2018-07-14T13:30:12.435",
        "name": "Project 2",
        "description": "",
        "start_date": "2018-07-01T17:14:07",
        "end_date": "2018-07-10T17:14:07",
        "creator": {
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
        "status": null
    }
}
```

## Get Project

Attribute | Default | Description
--------- | ------- | -----------
project_id | None | Id of the project.

Only open projects can be fetched by this API.


> Request
>
> GET project/[project_id]/

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Project details fetched",
    "data": {
        "id": 1,
        "creation_date": "2018-07-14T13:29:27",
        "name": "Sucees Project",
        "description": "Test this description",
        "start_date": "2019-06-01T17:14:07",
        "end_date": "2018-07-10T17:14:07",
        "creator": {
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
        "status": null,
        "managers": [
            {
                "id": 5,
                "logged_in": false,
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
            {
                "id": 7,
                "logged_in": true,
                "username": "anurag5",
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
        "members": []
    }
}
```

## Update Project

Attribute | Default | Description
--------- | ------- | -----------
project_id | None | Id of the project.
name | Null | A new name for the project.
description | Null | A new description for the project.
start_date | Null | Changed start_date, not more than a year from today's date.
end_date | Null | Changed end_date, not more than a decade from today's date.

Only send the parameter which needs to be updated. For example, to update the project name only send `name` param and its corresponding new value.

> Request
>
> PUT project/[project_id]/

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
    "message": "Updated",
    "data": {
        "id": 1,
        "creation_date": "2018-07-14T13:29:27",
        "name": "Test Projet Success",
        "description": "Test this description",
        "start_date": "2018-07-01T17:14:07",
        "end_date": "2018-07-10T17:14:07",
        "creator": {
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
        "status": null
    }
}
```

## Delete Project

Attribute | Default | Description
--------- | ------- | -----------
project_id | None | Id of the project.


> Request
>
> DELETE project/[project_id]/

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Deleted project with id: 1",
    "data": {
        "id": 1,
        "creation_date": "2018-07-14T14:49:43",
        "name": "Project 3",
        "description": "",
        "start_date": "2019-07-01T17:14:07",
        "end_date": "2029-07-10T17:14:07",
        "creator": {
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
        "status": null
    }
}
```

## Add Members

Attribute | Default | Description
--------- | ------- | -----------
project_id | None | Id of the project.
managers | None | Array of integers(user_ids). Maximum length 20.


There will only be `Project Managers` added. No other members can be added with this API.
Other members of the project may be added while adding members to workgroups(refer [work groups](#group)).

<aside class="notice">
Note: Duplicate managers are not supported for one project. A manager can be added only once.
</aside>

> Request
>
> POST project/[project_id]/member

```json
{
	"managers": [5, 7]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Members added to project",
    "data": [
        {
            "id": 5,
            "logged_in": false,
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
    ]
}
```

## Remove Members

Attribute | Default | Description
--------- | ------- | -----------
project_id | None | Id of the project
managers | None | Array of integers(user_ids). Maximum length 20.

Only if the user_id is part of the project will the user be removed, otherwise not.

> Request
>
> PUT project/[project_id]/member

```json
{
	"managers": [15, 19, 23]
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

Attribute | Default | Description
--------- | ------- | -----------
filter_by | ON_GOING | Filters that can be applied on the projects 
fromId    | 1       | Start range
toId      | 20      | End range

Following filters are available:

* ON_GOING - Currently active projects
* COMPLETED - All projects marked as complete
* FAV - All favourited projects by a user

Attributes must be provided as params.

<aside class="notice">
Note: Range between <code>fromId</code> and <code>toId</code> cannot be greater than 20.
</aside>

User with `View all projects` permission(admin) can see all projects in the organisation else
others will see only projects they are involved in.

> Request
>
> GET project/all/

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Projects found",
    "data": {
        "data_list": [
            {
                "id": 2,
                "creation_date": "2018-07-14T13:30:12",
                "name": "Project 2",
                "description": "",
                "start_date": "2018-07-01T17:14:07",
                "end_date": "2020-07-01T17:14:07",
                "creator": {
                    "info": "creator personal business info"
                },
                "status": null,
                "favourite": false,
                "managers": [
                    {
                        "info": "user's personal business info"
                    }
                ]
            },
            {
                "id": 3,
                "creation_date": "2018-07-14T14:31:50",
                "name": "Project 3",
                "description": "",
                "start_date": "2018-05-10T17:14:07",
                "end_date": "2021-07-01T17:14:07",
                "creator": {
                    "info": "creator personal business info"
                },
                "status": null,
                "favourite": true,
                "managers": [
                    {
                        "info": "user's personal business info"
                    },
                    {
                       "info": "user's personal business info" 
                    }
                ]
            }
        ]
    }
}
```

## Mark projects as complete

Attribute | Default | Description
--------- | ------- | -----------
projects  | None    | Array of integers(project_ids). Maximum length 20.


> Request
>
> PUT project/action/complete

```json
{
    "projects": [1]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Projects complete !"
}
```

## Mark projects as favourite

Attribute | Default | Description
--------- | ------- | -----------
projects  | None    | Array of integers(project_ids). Maximum length 20.


> Request
>
> POST project/action/favourite

```json
{
    "projects": [2, 3]
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
            "info": "user's personal business info" 
        },
        "projects": [
            {
                "id": 2,
                "creation_date": "2018-07-14T13:30:12",
                "name": "Project 2",
                "description": "",
                "start_date": "2018-07-01T17:14:07",
                "end_date": "2018-07-10T17:14:07",
                "creator": {
                    "info": "creator personal business info"
                },
                "status": null
            },
            {
                "id": 3,
                "creation_date": "2018-07-14T14:31:50",
                "name": "Project 3",
                "description": "",
                "start_date": "2019-07-01T17:14:07",
                "end_date": "2018-07-10T17:14:07",
                "creator": {
                    "info": "creator personal business info"
                },
                "status": null
            }
        ]
    }
}
```

## Mark projects as unfavourite

Attribute | Default | Description
--------- | ------- | -----------
projects  | None    | Array of integers(project_ids). Maximum length 20.


> Request
>
> PUT project/action/unfavourite

```json
{
    "projects": [1]
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

## Project Activity

Attribute | Default | Description
--------- | ------- | -----------
project_id| None    | Id of the project
fromId    | 1       | Start range
toId      | 20      | End range

Fetch the activity pertaining to a project.

Attributes must be provided as params.

<aside class="notice">
Note: Range between <code>fromId</code> and <code>toId</code> cannot be greater than 20.
</aside>

> Request
>
> GET project/[project_id]/activity

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Project activity fetched",
    "data": {
        "data_list": [
            "user x created project Project ....",
            "user x updated project details for Project ....",
            "user y added user z  as manager for Project ....",
            "user y added user z  as manager for Project ....",
            "user x removed some managers from project Project ...."
        ]
    }
}
```