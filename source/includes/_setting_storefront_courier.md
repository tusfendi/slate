# Setting Storefront Courier
## Get Active Couriers
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "Regular": [
      {
        "id": 1,
        "logistic_name": "JNE",
        "rate_name": "REG",
        "is_active": false
      },
      {
        "id": 8,
        "logistic_name": "RPX",
        "rate_name": "RGP",
        "is_active": true
      },
      {
        "id": 700,
        "logistic_name": "Tiki",
        "rate_name": "ECO",
        "is_active": true
      },
      {
        "id": 900,
        "logistic_name": "SAP",
        "rate_name": "UDRREG",
        "is_active": true
      },
      {
        "id": 902,
        "logistic_name": "SAP",
        "rate_name": "DRGREG",
        "is_active": true
      },
      {
        "id": 903,
        "logistic_name": "SiCepat",
        "rate_name": "SIUNT",
        "is_active": true
      },
      {
        "id": 915,
        "logistic_name": "J-Xpress",
        "rate_name": "Regular",
        "is_active": true
      },
      {
        "id": 921,
        "logistic_name": "iDExpress",
        "rate_name": "STD",
        "is_active": true
      }
    ],
    "Express": [
      {
        "id": 2,
        "logistic_name": "JNE",
        "rate_name": "YES",
        "is_active": false
      },
      {
        "id": 10,
        "logistic_name": "JNE",
        "rate_name": "CTCYES",
        "is_active": false
      },
      {
        "id": 11,
        "logistic_name": "RPX",
        "rate_name": "NDP",
        "is_active": true
      },
      {
        "id": 42,
        "logistic_name": "Lion Parcel",
        "rate_name": "ONEPACK",
        "is_active": true
      },
      {
        "id": 52,
        "logistic_name": "Tiki",
        "rate_name": "ONS",
        "is_active": true
      }
    ],
    "Trucking": [
      {
        "id": 363,
        "logistic_name": "Sicepat",
        "rate_name": "GOKIL",
        "is_active": false
      }
    ]
  }
}
```
Get list of account active couriers.

### Endpoint
`GET https://api.ngorder.id/api/open/setting/courier`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token








## Get Custom Couriers
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "name": "KURIR TOKO",
      "fee": 30000
    },
    {
      "id": 2,
      "name": "INDAH KARGO",
      "fee": 40000
    }
  ]
}
```
Get list of your shop custom couriers.

### Endpoint
`GET https://api.ngorder.id/api/open/setting/courier/custom`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token






## Update Courier Active Status
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "data has been successfully saved",
  "data": {
    "id": 1,
    "is_active": false
  }
}
```
Update courier activation status.

### Endpoint
`PATCH https://api.ngorder.id/api/open/setting/courier`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | string | Courier ID
is_active `(optional)` | boolean | Active status. Default value: `false`






## Update Couriers Active Status
> Example request:

```json
{
  "regular": [
    "4",
    "8",
    "15"
  ],
  "express": [
    "11",
    "42",
    "52",
    "56"
  ],
  "trucking": []
}
```

> Example response:

```json
{
  "response": "Success",
  "message": "data has been successfully saved",
  "data": {
    "regular": [
      "4",
      "8",
      "15"
    ],
    "express": [
      "11",
      "42",
      "52",
      "56"
    ],
    "trucking": []
  }
}
```
Update active status on multiple couriers. All IDs are taken from [Get Expeditions](#get-expeditions)

### Endpoint
`PATCH https://api.ngorder.id/api/open/setting/courier/all`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
regular `(optional)` | []string | Regular couriers ID 
express `(optional)` | []string | Express couriers ID
trucking `(optional)` | []string | Trucking couriers ID





## Update Custom Courier
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 7
  }
}
```
Update custom courier details.

### Endpoint
`PATCH https://api.ngorder.id/api/open/setting/courier/custom`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Custom courier ID taken from [Custom Couriers](#get-custom-couriers)
name | string | Custom courier name
fee | integer | Custom courier cost






## Delete Custom Courier
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "Data has been deleted",
  "data": {
    "id": 7
  }
}
```
Delete a custom courier.

### Endpoint
`DELETE https://api.ngorder.id/api/open/setting/courier/custom/{id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Custom courier ID taken from [Custom Couriers](#get-custom-couriers)