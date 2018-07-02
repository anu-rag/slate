# Users

## Fetch All Users

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.

> Request
>
> GET user/all?user_id=15

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Users found",
    "data": {
        "users": [
            {
                "id": 11,
                "username": "",
                "name": ""
            },
            {
                "id": 15,
                "username": "anu",
                "name": ""
            },
            {
                "id": 34,
                "username": "anurag15",
                "name": ""
            }
        ]
    }
}
```

## Add Role

Parameter | Default | Description
--------- | ------- | -----------
role | None | Id of the role.

The `user_id` is an unique integer identifier for a role.

> Request
>
> PUT user/[user_id]/role

```json
{
	"role": 3
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "User Role saved!"
}
```

## Remove Role

Parameter | Default | Description
--------- | ------- | -----------
role_id | None | Id of the role.

The `user_id` is an unique integer identifier for a role.

> Request
>
> DELETE user/[user_id]/role?role=[role_id]

```json
{
	"role": 3
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "User removed from role!"
}
```