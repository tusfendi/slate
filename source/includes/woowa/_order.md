# Woowa Order
## Send Message
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "Message sent successfully",
  "data": {
    "text": "Halo kak ANGGA DWI, sedang ada promo 35% untuk semua produk dan varian",
    "msid": "",
    "status": 1
  }
}
```
Send message for an order.

### Endpoint
`POST https://api.ngorder.id/api/open/woowa/order/message`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID taken from [Get Orders](#get-orders)
message | string | Message template text




## Get Message
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "id": 27,
    "type": "PROMO",
    "title": "Kirim Promo",
    "customer_phone": "082336440033",
    "message": "Halo kak ANGGA DWI, sedang ada promo 35% untuk semua product dan varian"
  }
}
```
Get an order message.

### Endpoint
`GET https://api.ngorder.id/api/open/woowa/order/message`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID taken from [Get Orders](#get-orders)
type `(optional)` | string | Message type. Available values: `REMINDER`, `ORDER_PROCESSED`, `ORDER_COMPLETED`, `ORDER_CANCELED` or `PROMO`. Default value: `REMINDER`




## Get Messages
> Example request:

```json
```

> Example response:

```json
```
Get multiple order messages.

### Endpoint
`GET https://api.ngorder.id/api/open/woowa/order/messages/{order_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
order_id | integer | Order ID taken from [Get Orders](#get-orders)