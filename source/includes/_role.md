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
                "name": "Create a task",
                "description": null
            },
            {
                "id": 2,
                "name": "Create a project",
                "description": null
            },
            {
                "id": 3,
                "name": "Create a user",
                "description": null
            },
            {
                "id": 4,
                "name": "Project Complete",
                "description": null
            },
            {
                "id": 5,
                "name": "Delete a user",
                "description": null
            },
            {
                "id": 6,
                "name": "Cretae Project Team",
                "description": null
            },
            {
                "id": 7,
                "name": "Close a task",
                "description": null
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