# Role

<aside class="notice">
This is a very delicate section which governs the hierarchy of the organisation. Care must be taken while using thses APIs.
</aside>

## Create Role

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
parent | Null | Id of the parent under which this role will be created.
name | Null | The name of the role to be kept. Maximum character length 250.
description | Null | The description of the role. Maximum character length 500.

<aside class="warning">
Care must be taken while creating roles. If a parent is not provided, then the new role created will be at the same level as of level 1(assuming level 1 > level 2 > .....) users. This may disturb the whole hierarchy.
</aside>

> Request
>
> POST role/create

```json
{
	"user_id": 15,
	"name": "project manager",
	"description": null,
	"parent": 2
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Role created!",
    "data": {
        "role": 3
    }
}
```

## Update Role

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
parent | Null | Id of the parent under which this role will be moved.
name | Null | The new name of the role to be kept.
description | Null | The new description of the role.

The `role_id` is an unique integer identifier for a role.

Only send the parameter which needs to be updated. For example, to update the project name only send `name` param and its corresponding new value.

<aside class="notice">
If the <code>role_id</code> is that of a root node(No roles above this role) then, even if the parent is supplied, the parent won't be updated.
</aside>

> Request
>
> PUT role/[role_id]

```json
{
	"user_id": 15,
	"name": "admin",
	"parent": 2
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Updated",
    "data": {
        "role": {
            "id": 3,
            "name": "admin",
            "description": null,
            "parent": 2
        }
    }
}
```

## Delete Role

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.

The `role_id` is an unique integer identifier for a role. 

> Request
>
> DELETE role/[role_id]?user_id=15

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Deleted"
}
```

## Fetch All Roles

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.

> Request
>
> GET role/list?user_id=15

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Roles found!",
    "data": {
        "roles": [
            {
                "id": 1,
                "name": "admin",
                "description": null
            },
            {
                "id": 2,
                "name": "project manager",
                "description": null
            }
        ]
    }
}
```

# Perms

List of available permissions with code:

name                             | code           
---------------------------------|----------------
Create a project                 | PJ_CR          
Edit a project                   | PJ_UP          
Delete a project                 | PJ_DL          
View a project                   | PJ_RD          
Project Complete                 | PJ_CMP         
Close Project                    | PJ_CL          
Create a user                    | USR_CR         
Delete a user                    | USR_DL         
Update User Business Information | USR_UP_BI_INFO 
Update User Personal Information | USR_UP_PR_INFO 
View User Business Information   | USR_RD_BI_INFO 
View User Personal Information   | USR_RD_PR_INFO 
Create team in Project           | GR_CR          
Update team in Project           | GR_UP          
Delete team in Project           | GR_DL          
View team in Project             | GR_RD          
Create a task                    | TK_CR          
Update a task                    | TK_UP          
Delete a task                    | TK_DL          
View a task                      | TK_RD          
Rate a task                      | TK_RT          
Close a task                     | TK_CL          
Follow all tasks                 | TK_FLA         
View Reports                     | RP_RD          
Create role                      | RL_CR          
Update role                      | RL_UP          
Delete role                      | RL_DL          
View role                        | RL_RD          
Assign role                      | RL_ASGN        

## Get All Permissions

This API can be used to retrieve permissions regargding a specific role, and also for fetching all the permissions available.
If `role` is provided then permissions for this `role` will only be fetched.
`role` can be provided as part of query params.

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
role | None | Id of the role.

> Request
>
> GET role/action?user_id=15

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Actions found!",
    "data": {
        "actions": [
            {
                "id": 1,
                "name": "Create a project",
                "description": null,
                "code": "PJ_CR"
            },
            {
                "id": 2,
                "name": "Edit a project",
                "description": null,
                "code": "PJ_UP"
            },
            {
                "id": 3,
                "name": "Delete a project",
                "description": null,
                "code": "PJ_DL"
            },
            {
                "id": 4,
                "name": "View a project",
                "description": null,
                "code": "PJ_RD"
            },
            {
                "id": 5,
                "name": "Project Complete",
                "description": null,
                "code": "PJ_CMP"
            }
        ]
    }
}
```

## Save Permissions

This API is used for saving permissions for a specific role.

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
role | None | Id of the role.
action_list | None | Array of integers(permission IDs).

> Request
>
> POST role/action

```json
{
	"user_id": 15,
	"role": 1,
	"action_list": [1, 2, 3, 4]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Actions saved for role!"
}
```