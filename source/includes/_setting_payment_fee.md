# Setting Payment Fee
## Create an Admin Fee
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 262,
    "nominal": "1200",
    "category_code": "1"
  }
}
```
Create an admin fee.

### Endpoint
`POST https://api.ngorder.id/api/open/setting/payment/admin-fee`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
nominal | integer | Admin fee nominal. Max `4500`
catgory_code | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](#get-categories-2)







## Get Admin Fees
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "id": 103,
      "nominal": 1500,
      "customer_category": {
        "code": "Y",
        "name": "Reseller"
      }
    },
    {
      "id": 104,
      "nominal": 4500,
      "customer_category": {
        "code": "N",
        "name": "Pelanggan"
      }
    },
    {
      "id": 115,
      "nominal": 2000,
      "customer_category": {
        "code": "D",
        "name": "Dropshipper"
      }
    },
    {
      "id": 262,
      "nominal": 1000,
      "customer_category": {
        "code": "1",
        "name": "Harga Teman"
      }
    }
  ]
}
```
Get list of admin fees.

### Endpoint
`GET https://api.ngorder.id/api/open/setting/payment/admin-fee`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token







## Update an Admin Fee
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 262,
    "nominal": "1200",
    "category_code": "1"
  }
}
```
Update an admin fee.

### Endpoint
`PATCH https://api.ngorder.id/api/open/setting/payment/admin-fee`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Admin fee ID taken from [Get Admin Fees](#get-admin-fees)
nominal | integer | Admin fee nominal. Max `4500`
catgory_code | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [Customer Categories](#get-categories-2)







## Get Xendit Data
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "xendit_key": "xnd_development_OImJfL8g1bHnM84L7EcTDeWY4OmqNUolCC2RxnmLWrelCwZhg",
    "is_xendit_active": true,
    "bank_support": [
      {
        "id": 26137,
        "name": "Mandiri Virtual Accounts",
        "holder_name": "NgorderID",
        "bank_number": null,
        "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/mandiri.png"
      },
      {
        "id": 26206,
        "name": "BNI Virtual Accounts",
        "holder_name": "NgorderID",
        "bank_number": null,
        "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bni.png"
      },
      {
        "id": 26207,
        "name": "Permata Virtual Accounts",
        "holder_name": "NgorderID",
        "bank_number": null,
        "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/permata.png"
      },
      {
        "id": 26208,
        "name": "BRI Virtual Accounts",
        "holder_name": "NgorderID",
        "bank_number": null,
        "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bri.png"
      }
    ]
  }
}
```
Get detailed Xendit data.

### Endpoint
`GET https://api.ngorder.id/api/open/setting/payment/xendit`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token







## Update Xendit Key
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "Payment settings were successfully updated",
  "data": {
    "xendit_key": "xnd_development_OImJfL8g1bHnM84L7EcTDeWY4OmqNUolCC2RxnmLWrelCwZhg"
  }
}
```
Update Xendit key.

### Endpoint
`PATCH https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
xendit_key | string | Xendit key taken from [Get Xendit Data](#get-xendit-data)