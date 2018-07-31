# Role

<aside class="notice">
This is a very delicate section which governs the hierarchy of the organisation. Care must be taken while using thses APIs.
</aside>

## Create Role

Attribute | Default | Description
--------- | ------- | -----------
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
    "name": "HOD",
    "description": "Head Of Department",
    "parent": 2
}
```

> Response

```json
{
    "status_code": 201,
    "status_text": "Created",
    "message": "Role created!",
    "data": {
        "id": 7,
        "name": "HOD",
        "description": "Head Of Department",
        "status": "ACTIVE",
        "parent": {
            "id": 2,
            "name": "sub-admin",
            "description": "Admin Delegate"
        }
    }
}
```

## Update Role

Attribute | Default | Description
--------- | ------- | -----------
parent | Null | Id of the parent under which this role will be moved.
name | Null | The new name of the role to be kept.
description | Null | The new description of the role.
role_id | None | An unique integer identifier for a role.


Only send the parameter which needs to be updated. For example, to update the project name only send `name` param and its corresponding new value.

<aside class="notice">
If the <code>role_id</code> is that of a root node(No roles above this role) then, even if the parent is supplied, the parent won't be updated.
</aside>

> Request
>
> PUT role/[role_id]

```json
{
    "name": "HR",
    "parent": 1
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Updated",
    "data": {
        "id": 7,
        "name": "HR",
        "description": "Head Of Department",
        "status": "ACTIVE",
        "parent": {
            "id": 1,
            "name": "Admin",
            "description": "Dev Admin"
        }
    }
}
```

## Delete Role

Attribute | Default | Description
--------- | ------- | -----------
role_id | None | An unique integer identifier for a role.


> Request
>
> DELETE role/[role_id]

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Deleted",
    "data": {
        "id": 7,
        "name": "HR",
        "description": "Head Of Department",
        "status": "DELETED",
        "parent": {
            "id": 1,
            "name": "Admin",
            "description": "Dev Admin"
        }
    }
}
```

## Get All Roles

This API can be used to fetch all 'ACTIVE' roles defined with the permissions for the corresponding roles.

Attribute | Default  | Description
--------- | -------- | -----------
fromId    | 1        | Start range
toId      | 20       | End range

Attributes must be provided as params.
Range between `fromId` and `toId` cannot be greater than 20.


> Request
>
> GET role/list

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Roles found!",
    "data": {
        "data_list": [
            {
                "id": 1,
                "name": "Admin",
                "description": "Dev Admin",
                "status": "ACTIVE",
                "parent": {},
                "permissions": [
                    {
                        "id": 1,
                        "name": "Create a project",
                        "description": null,
                        "code": "PJ_CR",
                        "checked": false
                    },
                    {}
                ]
            },
            {
                "id": 2,
                "name": "sub-admin",
                "description": "Admin Delegate",
                "status": "ACTIVE",
                "parent": {
                    "id": 1,
                    "name": "Admin",
                    "description": "Dev Admin"
                },
                "permissions": [
                    {
                        "id": 1,
                        "name": "Create a project",
                        "description": null,
                        "code": "PJ_CR",
                        "checked": false
                    },
                    {}
                ]
            },
            {},
            {}
        ]
    }
}
```

## Role Hierarchy

This API is for fetching role hierarchy in the system.

> Request
>
> GET role/hierarchy

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Roles hierarchy",
    "data": {
        "id": 1,
        "name": "Admin",
        "description": "Dev Admin",
        "status": null,
        "parent": {},
        "user_count": 1,
        "subordinates": [
            {
                "id": 2,
                "name": "sub-admin",
                "description": "Admin Delegate",
                "status": "ACTIVE",
                "parent": {
                    "id": 1,
                    "name": "Admin",
                    "description": "Dev Admin"
                },
                "user_count": 1,
                "subordinates": [
                    {
                        "id": 3,
                        "name": "HR",
                        "description": "Admin Delegate",
                        "status": "ACTIVE",
                        "parent": {
                            "id": 2,
                            "name": "sub-admin",
                            "description": "Admin Delegate"
                        },
                        "user_count": 0,
                        "subordinates": []
                    },
                    {
                        "id": 5,
                        "name": "HOD",
                        "description": "Head Of Department: Civil",
                        "status": "ACTIVE",
                        "parent": {
                            "id": 2,
                            "name": "sub-admin",
                            "description": "Admin Delegate"
                        },
                        "user_count": 0,
                        "subordinates": [
                            {
                                "id": 8,
                                "name": "Chief Engineer",
                                "description": "Chief Engineer for the department",
                                "status": "ACTIVE",
                                "parent": {
                                    "id": 5,
                                    "name": "HOD",
                                    "description": "Head Of Department: Civil"
                                },
                                "user_count": 0,
                                "subordinates": [
                                    {
                                        "id": 10,
                                        "name": "Union Leader",
                                        "description": "Union leader under Chief Engineer",
                                        "status": "ACTIVE",
                                        "parent": {
                                            "id": 8,
                                            "name": "Chief Engineer",
                                            "description": "Chief Engineer for the department"
                                        },
                                        "user_count": 0,
                                        "subordinates": []
                                    }
                                ]
                            },
                            {
                                "id": 9,
                                "name": "Chief Advisor",
                                "description": "Chief Advisor for the department",
                                "status": "ACTIVE",
                                "parent": {
                                    "id": 5,
                                    "name": "HOD",
                                    "description": "Head Of Department: Civil"
                                },
                                "user_count": 0,
                                "subordinates": []
                            }
                        ]
                    },
                    {
                        "id": 6,
                        "name": "HOD",
                        "description": "Head Of Department: CS",
                        "status": "ACTIVE",
                        "parent": {
                            "id": 2,
                            "name": "sub-admin",
                            "description": "Admin Delegate"
                        },
                        "user_count": 0,
                        "subordinates": []
                    }
                ]
            },
            {
                "id": 7,
                "name": "HR",
                "description": "Head Of Department",
                "status": "ACTIVE",
                "parent": {
                    "id": 1,
                    "name": "Admin",
                    "description": "Dev Admin"
                },
                "user_count": 1,
                "subordinates": []
            }
        ]
    }
}
```

# Perms

List of available permissions with code:

name                             | code           
---------------------------------|----------------
Create a user                    | USR_CR         
Delete a user                    | USR_DL         
Update User Business Information | USR_UP_BI_INFO 
Update User Personal Information | USR_UP_PR_INFO 
View User Business Information   | USR_RD_BI_INFO 
View User Personal Information   | USR_RD_PR_INFO 
Suspend a user                   | USR_SPND
Reset password for password      | USR_RE_PSWD
Create role                      | RL_CR          
Update role                      | RL_UP          
Delete role                      | RL_DL          
View role                        | RL_RD          
Assign role                      | RL_ASGN        
Assign permissions for role      | PERM_ASGN
Remove permissions for role      | PERM_RMV
Create a project                 | PJ_CR          
Edit a project                   | PJ_UP          
Delete a project                 | PJ_DL          
View a project                   | PJ_RD          
Project Complete                 | PJ_CMP         
Close Project                    | PJ_CL          
View all projects                | PJ_RD_ALL
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
View all tasks                   | TK_RD_ALL
View Reports                     | RP_RD          

## Get All Permissions

This API can be used to retrieve permissions regargding a specific role, and also for fetching all the permissions available.
If `role` is provided then permissions for this `role` will only be fetched.
`role` can be provided as part of query params.

Attribute | Default | Description
--------- | ------- | -----------
role | None | Id of the role.

> Request
>
> GET role/action

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Actions found!",
    "data": {
        "PJ_CR": {
            "id": 1,
            "name": "Create a project",
            "description": null,
            "code": "PJ_CR"
        },
        "PJ_UP": {
            "id": 2,
            "name": "Edit a project",
            "description": null,
            "code": "PJ_UP"
        },
        "PJ_DL": {
            "id": 3,
            "name": "Delete a project",
            "description": null,
            "code": "PJ_DL"
        },
        "PJ_RD": {
            "id": 4,
            "name": "View a project",
            "description": null,
            "code": "PJ_RD"
        },
        "PJ_CMP": {
            "id": 5,
            "name": "Project Complete",
            "description": null,
            "code": "PJ_CMP"
        },
        "PJ_CL": {
            "id": 6,
            "name": "Close Project",
            "description": null,
            "code": "PJ_CL"
        }
    }
        
}
```


> Request
>
> GET role/action?role=[role_id]

```json

```

> Response (when [role_id] is provided)

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Actions found!",
    "data": {
        "PJ_CR": {
            "id": 1,
            "name": "Create a project",
            "description": null,
            "code": "PJ_CR",
            "checked": true
        },
        "PJ_UP": {
            "id": 2,
            "name": "Edit a project",
            "description": null,
            "code": "PJ_UP",
            "checked": true
        },
        "PJ_DL": {
            "id": 3,
            "name": "Delete a project",
            "description": null,
            "code": "PJ_DL",
            "checked": true
        },
        "PJ_RD": {
            "id": 4,
            "name": "View a project",
            "description": null,
            "code": "PJ_RD",
            "checked": false
        },
        "PJ_CMP": {
            "id": 5,
            "name": "Project Complete",
            "description": null,
            "code": "PJ_CMP",
            "checked": true
        },
        "PJ_CL": {
            "id": 6,
            "name": "Close Project",
            "description": null,
            "code": "PJ_CL",
            "checked": false
        }
    }
        
}
```


## Save Permissions

This API is used for saving permissions for a specific role.

Attribute | Default | Description
--------- | ------- | -----------
role | None | Id of the role.
action_list | None | Array of integers(permission IDs).

> Request
>
> POST role/action

```json
{
	"role": 1,
	"action_list": [1, 2, 4]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Actions saved for role!",
    "data": {
        "PJ_CR": {
            "id": 1,
            "name": "Create a project",
            "description": null,
            "code": "PJ_CR",
            "checked": true
        },
        "PJ_UP": {
            "id": 2,
            "name": "Edit a project",
            "description": null,
            "code": "PJ_UP",
            "checked": true
        },
        "PJ_DL": {
            "id": 3,
            "name": "Delete a project",
            "description": null,
            "code": "PJ_DL",
            "checked": false
        },
        "PJ_RD": {
            "id": 4,
            "name": "View a project",
            "description": null,
            "code": "PJ_RD",
            "checked": true
        },
    
    }
}
```

## Remove Permissions

Attribute | Default | Description
--------- | ------- | -----------
role | None | Id of the role.
action_list | None | Array of integers(permission IDs).

> Request
>
> POST role/action

```json
{
    "role": 1,
    "action_list": [1, 2, 4]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Actions removed for role!"
}
```