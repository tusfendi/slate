# Order Source
## Create Order Source
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "order_source_id": 2980,
    "note": "Akirabutik"
  }
}
```
Create an order source

### Endpoint
`POST https://api.ngorder.id/api/open/order-source/create`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
marketplace_id | integer | Marketplace ID taken from [Marketplaces](#get-marketplaces)
note | string | Order source name

## Get Order Sources
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "id": 12,
      "marketplace_id": 5,
      "marketplace_name": "Whatsapp",
      "note": "085755065637",
      "status": "ACTIVE"
    },
    {
      "id": 30,
      "marketplace_id": 1,
      "marketplace_name": "Tokopedia",
      "note": "",
      "status": "ACTIVE"
    },
    {
      "id": 475,
      "marketplace_id": 3,
      "marketplace_name": "Shopee",
      "note": "Akira Butik & MukenaCantik77",
      "status": "ACTIVE"
    },
    {
      "id": 476,
      "marketplace_id": 3,
      "marketplace_name": "Shopee",
      "note": "Baju Branded Original",
      "status": "ACTIVE"
    },
    {
      "id": 477,
      "marketplace_id": 3,
      "marketplace_name": "Shopee",
      "note": "kadocoklat",
      "status": "ACTIVE"
    },
    {
      "id": 478,
      "marketplace_id": 3,
      "marketplace_name": "Shopee",
      "note": "Deandra Grosir Baju Anak",
      "status": "ACTIVE"
    }
  ]
}
```
Get order sources.

### Endpoint
` https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
status `(optional)` | string | Active status. Available values: `Y` or `N`

## Update Order Source
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "order_source_id": 2980,
    "note": "Akirabutik"
  }
}
```
Update an order source

### Endpoint
`PATCH https://api.ngorder.id/api/open/order-source/update`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
order_source_id | integer | Order source ID
marketplace_id `(optional)` | integer | Marketplace ID taken from [Marketplaces](#get-marketplaces)
note `(optional)` | string | Order source name
status `(optional)` | string | Active status. Available values: `Y` or `N`