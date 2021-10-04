# Supplier
Supplier is used as the origin of the shipping address
## Create Supplier
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "supplier_id": 1,
    "name": "Sejahtera Makmur"
  }
}
```
Create supplier.

### Endpoint
`POST https://api.ngorder.id/api/open/supplier/create`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
name | string | Supplier name
district_id | numeric | District ID taken from [Region](#region)
addess | string | Supplier detailed address
phone | numeric | Supplier phone number
description | string | Data description

## Get Suppliers
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "name": "Supplier 1",
      "district_id": 2087,
      "shipper_id": 4776,
      "district": "Cengkareng",
      "city_id": 151,
      "city": "Kota Jakarta Barat",
      "location": "Cengkareng, Kota Jakarta Barat",
      "phone": "08123456789",
      "address": "JL. ABC",
      "description": "",
      "shipper_status": "ACTIVE"
    },
    {
      "id": 2,
      "name": "Supplier 2",
      "district_id": 334,
      "shipper_id": 11677,
      "district": "Ranca Bali",
      "city_id": 22,
      "city": "Kabupaten Bandung",
      "location": "Ranca Bali, Kabupaten Bandung",
      "phone": "08123456789",
      "address": "JL. ABC",
      "description": "",
      "shipper_status": "ACTIVE"
    }
  ]
}
```
Get all suppliers.
### Endpoint
`GET https://api.ngorder.id/api/open/supplier`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

## Update Supplier
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "supplier_id": 1,
    "name": "Sejahtera Makmur"
  }
}
```
Update supplier data.

### Endpoint
` https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
supplier_id | integer | Supplier ID
name `(optional)` | string | Supplier name
district_id `(optional)` | numeric | District ID taken from [Region](#region)
addess `(optional)` | string | Supplier detailed address
phone `(optional)` | numeric | Supplier phone number
description `(optional)` | string | Data description