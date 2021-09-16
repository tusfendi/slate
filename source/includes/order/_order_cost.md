# Order Cost
## Create Order Cost
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "order_cost_id": "5f154995060c000047005b6c",
    "name": "Diskon Ultah"
  }
}
```
Create an order cost

### Endpoint
`POST https://api.ngorder.id/api/open/order-cost/create`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
category | string | Order cost category. Available values: `DISCOUNT` or `OTHER COST`
name | string | Order cost name
type | string | Order cost type. Available values: `NOMINAL` or `PERCENTAGE`
nominal | integer | Order cost nominal. Required if `type: NOMINAL`
percentage `(optional)` | integer | Order cost percentage. Required if `type: PERCENTAGE`


## Get Order Costs
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "order_cost_id": "5ee966002dcc1277122556c7",
      "title": "Diskon Order",
      "category": "OTHER COST",
      "type": "NOMINAL",
      "name": "Biaya Lain",
      "percentage": 0,
      "nominal": 1000
    },
    {
      "order_cost_id": "5f08080d89ecff22732f9df2",
      "title": "Diskon Order",
      "category": "DISCOUNT",
      "type": "NOMINAL",
      "name": "Diskon",
      "percentage": 0,
      "nominal": 10000
    },
    {
      "order_cost_id": "5f18e505ff430000f1003b84",
      "title": "Diskon Order",
      "category": "DISCOUNT",
      "type": "PERCENTAGE",
      "name": "Diskon Lagi",
      "percentage": 50,
      "nominal": 1500
    }
  ]
}
```
Get all order costs.

### Endpoint
`GET https://api.ngorder.id/api/open/order-cost`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

## Update Order Cost
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "order_cost_id": "5f154995060c000047005b6c",
    "name": "Diskon Ultah"
  }
}
```
Update an order cost

### Endpoint
`PUT https://api.ngorder.id/api/open/order-cost/update`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
order_cost_id | integer | Order cost ID
category `(optional)` | string | Order cost category. Available values: `DISCOUNT`, `OTHER` or `COST`
name `(optional)` | string | Order cost name
nominal `(optional)` | integer | Order cost nominal. Required if `type: NOMINAL`
percentage `(optional)` | integer | Order cost percentage. Required if `type: PERCENTAGE`
type `(optional)` | string | Order cost type. Available values: `NOMINAL` or `PERCENTAGE`. Required if `nominal` or `percentage` is not `null`

## Delete Order Cost
> Example request:

```json
```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "order_cost_id": "5f154995060c000047005b6c",
    "name": "Diskon Ultah"
  }
}
```
Create an order cost

### Endpoint
`POST https://api.ngorder.id/api/open/order-source/delete/{order_cost_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
order_cost_id | integer | Order cost ID