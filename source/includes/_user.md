# User
## Get Users
> Example response:

```json
{
  "response": "Success",
  "data": [
    {
      "id": 1,
      "name": "User One",
      "email": "user1@example.com"
    },
    {
      "id": 2,
      "name": "User Two",
      "email": "user2@example.com"
    },
  ]
}
```

Get user all users data within your shop

### Endpoint
`GET https://api.ngorder.id/api/open/user

### Header
Parameter | type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

## Update Profile
> Example response:

```json
{
  "response": "success",
  "data": {
    "full_name": "User 1",
    "phone_number": "0812345678"
  }
}
```

### Endpoint
`PATCH https://api.ngorder.id/api/open/user/profile`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
full_name | string | User full name
phone_number | numeric | User phone number
password `(optional)` | string | User password
password_confirmation `(optional)` | string | User password confirmation. Required if `password` is filled.