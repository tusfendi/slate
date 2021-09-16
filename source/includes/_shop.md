# Shop
## Get Detail
> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "username": "toko123",
      "shop_name": "Tokoku",
      "status": "ACTIVE",
      "class": "PLATINUM",
      "join_date": "2016-01-25",
      "expired_date": "2022-05-01",
      "phone": "08123445566",
      "courier": "JNE,TIKI,POS,SICEPAT,WAHANA,JNT",
      "address": "Indonesia",
      "shipper_status": "NON ACTIVE",
      "note": null,
      "store_front": true,
      "warehouse": true,
      "users": [
        {
          "id": 1,
          "email": "juragan@ngorder.id",
          "name": "Juragan"
        },
        {
          "id": 2,
          "email": "admin1@ngorder.id",
          "name": "Admin"
        }
      ],
      "active_supplier": {
        "id": 1,
        "name": "Good Supplier",
        "location": "Malang",
        "phone": "0812345678",
        "address": "JL. ABC No. 123",
        "note": ""
      }
    }
  ]
}
```

### Endpoint
`GET https://api.ngorder.id/api/open/shop`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

## Update Detailed Info
> Example response:

```json
{
  "response": "Success",
  "data": {
    "shop_id": 1
  }
}
```
Update your shop info.

### Endpoint
`PATCH https://api.ngorder.id/api/open/shop/update`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
shop_name | string | Shop name
subdomain | string | Subdomain used in Ngorder
phone | numeric | Shop phone number
name | string | Account name
description `(optional)` | string | Shop description

## Upload Logo
> Example response:

```json
{
  "response": "Success",
  "data": {
    "logo": "https://ngorder-1.sgp1.digitaloceanspaces.com/7/logo/logo-1606963029075.png"
  }
}
```
Upload shop logo.

### Endpoint
`PATCH https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
logo | image | Shop logo. Max size 2MB

## Update General Info
> Example response:

```json
{
  "response": "Success",
  "message": "General info successfully updated",
  "data": {
    "shop_name": "Tokoku",
    "address": "JL. ABC No. 123",
    "description": "Toko serbaguna",
    "phone": "0812345678",
    "logo": "https://ngorder-1.sgp1.digitaloceanspaces.com/7/logo/logo-1606963029075.png"
  }
}
```
Update general shop info.

### Endpoint
`PATCH https://api.ngorder.id/api/open/shop/general`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
shop_name | string | Shop name
phone | string | Shop phone number
description | string | Shop description
address | string | Shop address
logo | string | Shop logo url