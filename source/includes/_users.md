# Users

## Create User

Attribute | Default | Description
--------- | ------- | -----------
username            | None    | Username for the user. Maximum character length 128.
password            | None    | Password for the user
first_name          | None    | First name of the user. Maximum character length 30.
last_name           | None    | Surname of the user. Maximum character length 30.
personal_email      | None    | Email of the user. Maximum character length 254.
mobile              | NULL    | Personal phone number of the user.
emergency_contact   | NULL    | Contact number of the person in case of emergency.
permanent_address   | NULL    | Address field. Maximum character length 500.
current_address     | NULL    | Address field. Maximum character length 500.
interests           | NULL    | User intersts. Address field. Maximum character length 200.
company_name        | NULL    | Company name of the employee. Maximum character length 500.
work_email          | NULL    | Email of the user. Maximum character length 254.
contact_number      | NULL    | Company provided mobile number, if so.
employee_id         | NULL    | Unique identifier for the employee in the company. Maximum character length 250.
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
    "employee_id": "unique_employee_id",
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
        },
        "token": {
            "token": "AveEEeeeEeeeEEeEEeEEERYLoOOoOOoOONnnNNnNnNnGGGgAcEssToKEn",
            "expires_at": 1531397477
        }
    }
}
```

## Get User

Attribute | Default | Description
--------- | ------- | -----------
emp_user_id | None | Id of the user whose details need to be fetched.


> Request
>
> GET user/[emp_user_id]/

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
}
```

## Update User

Attribute | Default | Description
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
company_name        | NULL    | Company name of the employee. Maximum character length 500.
work_email          | NULL    | Email of the user. Maximum character length 254.
contact_number      | NULL    | Company provided mobile number, if so.
employee_id         | NULL    | Unique identifier for the employee in the company. Maximum character length 250.
designation         | NULL    | Designation of the user.
department          | NULL    | Department of the user.
blood_group         | NULL    | Blood group of teh user.
date_of_joining     | NULL    | Date field. No time component.
availability        | NULL    | If the user(as a resource) is available.

Only send the parameter which needs to be updated. For example, to update the first name only send `first_name` param and its corresponding new value.

Updating Business Information requires an additional permission. If the requesting user has this permission, then they will be able to update the business information.

<aside class="warning">
Note: Provide initial value along with additions for <code>interests</code> parameter, as the same would be updated.
If only the updated value is provided without initial then <code>interests</code> will only contain updated value
</aside>

> Request
>
> PUT user/[emp_user_id]/

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
            "interests": "hiking"
        },
        "business": {
            "company_name": null,
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

Attribute | Default | Description
--------- | ------- | -----------
emp_user_id | None | Id of the user whose details need to be deleted.

> Request
>
> DELETE user/[emp_user_id]/

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
}
```

## Fetch All Users

> Request
>
> GET user/all

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Users found",
    "data": {
        "data_list": [
            {
                "id": 40,
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
                "id": 41,
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
            }
        ]
    }
}
```

## Add Role

Attribute | Default | Description
--------- | ------- | -----------
emp_user_id | None | Id of the user who should be attached to the role.
role | None | Id of the role.

The `role` is an unique integer identifier for a role.

> Request
>
> PUT user/[emp_user_id]/role

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
    "message": "User Role saved!",
    "data": {
        "user": {
            "id": 40,
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
        "role": {
            "id": 3,
            "name": "HR",
            "description": "Admin Delegate",
            "status": "ACTIVE",
            "parent": {
                "id": 2,
                "name": "sub-admin",
                "description": "Admin Delegate"
            }
        }
    }
}
```

## Remove Role

Attribute | Default | Description
--------- | ------- | -----------
emp_user_id | None | Id of the user who should be removed from the role.
role_id | None | Id of the role.

The `role_id` is an unique integer identifier for a role.

> Request
>
> DELETE user/[emp_user_id]/role?role=[role_id]

```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "User removed from role!",
    "data": {
        "user": {
            "id": 40,
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
        "role": {
            "id": 3,
            "name": "HR",
            "description": "Admin Delegate",
            "status": "ACTIVE",
            "parent": {
                "id": 2,
                "name": "sub-admin",
                "description": "Admin Delegate"
            }
        }
    }
}
```

## Suspend Users

Attribute | Default | Description
--------- | ------- | -----------
users | None | List of user Ids

> Request
>
> PUT user/action/suspend

```json
{
    "users": [3]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Users suspended !"
}
```

## Activate Users

Attribute | Default | Description
--------- | ------- | -----------
users | None | List of user Ids

> Request
>
> PUT user/action/activate

```json
{
    "users": [3]
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Users activateed !"
}
```

## Resst Employee Password

This API is for admin side reset password.

Attribute | Default | Description
--------- | ------- | -----------
emp_user_id | None | Id of the user whose password needs to be reset.
password    | None | New password
re_password | None | Retype new password

> Request
>
> PUT user/[emp_user_id]/reset/password

```json
{
    "password": "new_password",
    "re_password": "new_password"
}
```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Password reset successful",
    "data": {
        "id": 40,
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
    }
}
```

## Users for a role

The API endpoint for [users for a role](#users-for-a-role), [users count for a role](#users-count-for-a-role), [users for all roles](#users-for-all-roles), [users count for each role](#users-count-for-all-roles) is same. This API can be used to:

* fetch users for a single role, provide only `role_id` 
* count of users for single role, provide `role_id` and `count`
* fetch all users for all roles defined, provide `all`
* count all users for all roles defined, provide `all` and `count`

These attributes are provided as GET params.

Get all users for a given role.

Attribute | Default | Description
--------- | ------- | -----------
role_id | None | Id of the role.

> Request
>
> GET user/role?role=[role_id]


```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Data fetched",
    "data": {
        "role": {
            "id": 1,
            "name": "Admin",
            "description": "Dev Admin",
            "status": null,
            "parent": {}
        },
        "users": [
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

## Users count for a role

Get user count for a given role.

Attribute | Default | Description
--------- | ------- | -----------
role_id   | None    | Id of the role.
count     | None    | true / false value

> Request
>
> GET user/role?role=[role_id]&count=true


```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Data fetched",
    "data": {
        "role": {
            "id": 1,
            "name": "Admin",
            "description": "Dev Admin",
            "status": null,
            "parent": {}
        },
        "count": 1
    }
}
```

## Users for all roles

Get all users for each role.

Attribute | Default | Description
--------- | ------- | -----------
all       | None    | true / false value

> Request
>
> GET user/role?all=true


```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Data fetched",
    "data": {
        "data_list": [
            {
                "role": {
                    "id": 1,
                    "name": "Admin",
                    "description": "Dev Admin",
                    "status": null,
                    "parent": {}
                },
                "users": [
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
            },
            {
                "role": {
                    "id": 2,
                    "name": "sub-admin",
                    "description": "Admin Delegate",
                    "status": "ACTIVE",
                    "parent": {
                        "id": 1,
                        "name": "Admin",
                        "description": "Dev Admin"
                    }
                },
                "users": []
            }
        ]
    }
}
```

## Users count for all roles

Get all users count for each role.

Attribute | Default | Description
--------- | ------- | -----------
all       | None    | true / false value
count     | None    | true / false value

> Request
>
> GET user/role?all=true&count=true


```json

```

> Response

```json
{
    "status_code": 200,
    "status_text": "Success. OK.",
    "message": "Data fetched",
    "data": {
        "data_list": [
            {
                "role": {
                    "id": 1,
                    "name": "Admin",
                    "description": "Dev Admin",
                    "status": null,
                    "parent": {}
                },
                "count": 1
            },
            {
                "role": {
                    "id": 2,
                    "name": "sub-admin",
                    "description": "Admin Delegate",
                    "status": "ACTIVE",
                    "parent": {
                        "id": 1,
                        "name": "Admin",
                        "description": "Dev Admin"
                    }
                },
                "count": 0
            }
        ]
    }
}
```