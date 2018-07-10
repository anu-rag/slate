# Users

## Create User

Parameter | Default | Description
--------- | ------- | -----------
user_id             | None    | Id of the user who is sending the request.
username            | None    | Username for the user. Maximum character length 128.
password            | None    | Password for the user
first_name          | None    | First name of the user. Maximum character length 30.
last_name           | None    | Surname of the user. Maximum character length 30.
personal_email      | None    | Email of the user. Maximum character length 254.
mobile              | NULL    |
emergency_contact   | NULL    | Contact number of the person in case of emergency.
permanent_address   | NULL    | Address field. Maximum character length 500.
current_address     | NULL    | Address field. Maximum character length 500.
interests           | NULL    | User intersts. Address field. Maximum character length 200.
work_email          | NULL    | Email of the user. Maximum character length 254.
contact_number      | NULL    | Company provided mobile number, if so.
employee_id         | NULL    | Unique identifier for the employee in the company.
designation         | NULL    | Designation of the user.
department          | NULL    | Department of the user.
location            | NULL    | Residing city of the user.
blood_group         | NULL    | Blood group of teh user.
date_of_joining     | NULL    | Date field. No time component.
linkedin_profile    | NULL    | URL field. LinkedIn URL.

<aside class="notice">
Note: <code>interests</code> is a comma-separated value.
</aside>

> Request
>
> POST user/create

```json
{
    "user_id": 15,
    "username": "username",
    "first_name": "first_name",
    "last_name": "last_name",
    "personal_email": "your@email.address",
    "password": "password",
    "mobile": "89XXXXXXX2",
    "emergency_contact": "67XXXXXX61",
    "permanent_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
    "current_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
    "interests": "music, art",
    "work_email": "work@email.address",
    "contact_number": "9XXXXXX31",
    "employee_id": "unique_id",
    "designation": "Department Head",
    "department": "Mechanical",
    "location": "Bangalore",
    "blood_group": "O+ve",
    "date_of_joining": "2015-07-11",
    "linkedin_profile": "https://url/to/linkedin/profile/"
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "User Created",
    "data": {
        "id": 40,
        "logged_in": false,
        "username": "username",
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
            "work_email": "work@email.address",
            "contact_number": "9XXXXXX31",
            "loaction": "Bangalore",
            "employee_id": "unique_id",
            "designation": "Department Head",
            "department": "Mechanical",
            "blood_group": "O+ve",
            "date_of_joining": "2015-07-11",
            "linkedin_profile": "https://url/to/linkedin/profile/"
        },
        "token": {
            "token": "AveEEeeeEeeeEEeEEeEEERYLoOOoOOoOONnnNNnNnNnGGGgAcEssToKEn",
            "expires_at": 1531397477
        }
    }
}
```

## Get User

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
emp_user_id | None | Id of the user whose details need to be fetched.


> Request
>
> GET user/[emp_user_id]/?user_id=15

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "User details fetched",
    "data": {
        "id": 40,
        "logged_in": false,
        "username": "username",
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
}
```

## Update User

Parameter | Default | Description
--------- | ------- | -----------
emp_user_id         | None    | Id of the user whose details need to be updated.
first_name          | None    | First name of the user. Maximum character length 30.
last_name           | None    | Surname of the user. Maximum character length 30.
personal_email      | None    | Email of the user. Maximum character length 254.
mobile              | NULL    |
emergency_contact   | NULL    | Contact number of the person in case of emergency.
permanent_address   | NULL    | Address field. Maximum character length 500.
current_address     | NULL    | Address field. Maximum character length 500.
interests           | NULL    | User intersts. Address field. Maximum character length 200.
linkedin_profile    | NULL    | URL field. LinkedIn URL.
location            | NULL    | Residing city of the user.

Only send the parameter which needs to be updated. For example, to update the first name only send `first_name` param and its corresponding new value.

<aside class="warning">
Note: Provide initial value along with additions for <code>interests</code> parameter, as the same would be updated.
If only the updated value is provided without initial then <code>interests</code> will only contain updated value
</aside>

> Request
>
> PUT user/[emp_user_id]/?user_id=15

```json
{
    "location": "Banshankari",
    "interests": "hiking"
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Updated",
    "data": {
        "id": 40,
        "logged_in": false,
        "username": "username",
        "personal": {
            "email": "your@email.address",
            "first_name": "first_name",
            "last_name": "last_name",
            "full_name": "first_name last_name",
            "mobile_number": "89XXXXXXX2",
            "emergency_contact": "67XXXXXX61",
            "permanent_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
            "current_address": "#34, 11th Cross 3rd Main, Jayanagar 4th Block, Bangalore, Karnataka",
            "interests": "hiking"
        },
        "business": {
            "work_email": "work@email.address",
            "contact_number": "9XXXXXX31",
            "loaction": "Banshankari",
            "employee_id": "unique_id",
            "designation": "Department Head",
            "department": "Mechanical",
            "blood_group": "O+ve",
            "date_of_joining": "2015-07-11",
            "linkedin_profile": "https://url/to/linkedin/profile/"
        }
    }
}
```

## Delete User

Parameter | Default | Description
--------- | ------- | -----------
user_id | None | Id of the user who is sending the request.
emp_user_id | None | Id of the user whose details need to be deleted.

> Request
>
> DELETE user/[emp_user_id]/?user_id=15

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "User details fetched",
    "data": {
        "id": 40,
        "logged_in": false,
        "username": "username",
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
}
```

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

The `role_id` is an unique integer identifier for a role.

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

The `role_id` is an unique integer identifier for a role.

> Request
>
> DELETE user/[user_id]/role?role=[role_id]

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "User removed from role!"
}
```