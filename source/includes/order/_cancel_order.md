# Cancel Order
## Cancel an Order
> Example request:

```json
```

> Example response:

```json
{
  "response": "success",
  "message": "Order has been Canceled",
  "data": {
    "order_id": 1338,
    "po_number": 10735
  }
}
```
Cancel created order.

### Endpoint
`POST https://api.ngorder.id/api/open/order/cancel`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID taken from [Get Orders](#get-orders)








## Get Canceled Orders
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "order_id": 566,
      "po_number": 505,
      "username": "user",
      "invoice": "INV.2021.01.18.505",
      "shop_id": 7,
      "order_date": "2021-01-18 10:37:42",
      "sender_name": "Tusfendi",
      "sender_category": "PELANGGAN",
      "sender_category_code": "N",
      "sender_address": "Desa ABC",
      "receiver_name": "Tusfendi",
      "receiver_address": "Desa ABC, Kec. Srono, Kabupaten Banyuwangi, 68471, Jawa Timur",
      "receiver_phone": "0812345678",
      "total_amount": 0,
      "remaining_amount": 0,
      "shipping_id": 98,
      "shipping_rate": "",
      "shipping_logistic": "Ambil di Toko",
      "shipping_cost": 0,
      "weight": 2,
      "note": "",
      "origin_name": "A Supplier 1",
      "origin_address": "Jalan Bondowoso",
      "order_source": "",
      "other_cost_amount": 0,
      "order_progress_status": "NO AWB",
      "order_status": "CANCELED",
      "order_category": "APP",
      "payment_status": "PAID",
      "payment_date": "2021-01-18",
      "products": [
        {
          "product_meta_id": 8055339,
          "sku": null,
          "name": "Kaos Yes Biru",
          "price": 10000,
          "quantity": 10,
          "thumbnail_url": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
          "color": null,
          "size": null
        }
      ],
      "shopee": null,
      "created_by_name": "tusfendi",
      "created_at": "2021-01-18 10:37:42",
      "updated_by_name": "",
      "updated_at": "2021-01-18 10:37:42",
      "awb_number": "",
      "product_status": "S",
      "cost_of_goods_sales": 0,
      "order_cost": null,
      "bank_name": "Srono",
      "warehouse_name": null,
      "cod_status": false
    },
    {
      "order_id": 558,
      "po_number": 497,
      "username": "user",
      "invoice": "INV.2021.01.12.497",
      "shop_id": 1,
      "order_date": "2021-01-12 11:21:27",
      "sender_name": "Tusfendi",
      "sender_category": "PELANGGAN",
      "sender_category_code": "N",
      "sender_address": "Desa",
      "receiver_name": "Tusfendi",
      "receiver_address": "Desa, Kec. Srono, Kabupaten Banyuwangi, 68471, Jawa Timur",
      "receiver_phone": "0812345678",
      "total_amount": 0,
      "remaining_amount": 0,
      "shipping_id": 98,
      "shipping_rate": "",
      "shipping_logistic": "Ambil di Toko",
      "shipping_cost": 0,
      "weight": 2,
      "note": "",
      "origin_name": "A Supplier 1",
      "origin_address": "Jl. Abc",
      "order_source": "",
      "other_cost_amount": 0,
      "order_progress_status": "UNPAID",
      "order_status": "CANCELED",
      "order_category": "APP",
      "payment_status": "UNPAID",
      "payment_date": "2021-01-12",
      "products": [
        {
          "product_meta_id": 8055339,
          "sku": null,
          "name": "Kaos Yes",
          "price": 20000,
          "quantity": 10,
          "thumbnail_url": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
          "color": null,
          "size": null
        }
      ],
      "shopee": null,
      "created_by_name": "tusfendi",
      "created_at": "2021-01-14 11:21:27",
      "updated_by_name": "tusfendi",
      "updated_at": "2021-01-14 11:21:27",
      "awb_number": "",
      "product_status": "S",
      "cost_of_goods_sales": 0,
      "order_cost": null,
      "bank_name": null,
      "warehouse_name": null,
      "cod_status": false
    }
  ],
  "meta": {
    "pagination": {
      "total": 31,
      "count": 2,
      "per_page": 2,
      "current_page": 1,
      "total_pages": 16,
      "links": {
        "next": "https://api.ngorder.id/api/open/order-cancel?per_page=2&pagination_offset=2"
      }
    }
  }
}
```
Get list of canceled orders.

### Endpoint
`GET https://api.ngorder.id/api/open/order-cancel`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | string | Status of order data. Available values: `CANCEL`, `REJECTED` or `EXPIRED`. Default value: `CANCEL`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
per_page `(optional)` | integer | Data per page. Default value: `10`. Max `50`
pagination_offset `(optional)` | integer | Page number. Default value: `1`








## Download Canceled Orders
> Example request:

```json
```

> Example response:

```json

```
Download canceled, rejected or expired orders as Excel file.

### Endpoint
`GET https://api.ngorder.id/api/open/order-cancel/download`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | string | Status of order data. Available values: `CANCEL`, `REJECTED` or `EXPIRED`. Default value: `CANCEL`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`









## Return Canceled Order
> Example request:

```json
```

> Example response:

```json
```
Return canceled order as active order.

### Endpoint
`POST https://api.ngorder.id/api/open/order-cancel/return`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID taken from [Get Orders](#get-orders)








## Delete Canceled Order
> Example request:

```json
```

> Example response:

```json
```
Delete canceled order permanently.

### Endpoint
`DELETE https://api.ngorder.id/api/open/order-cancel/{order_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Canceled order ID taken from [Get Canceled Orders](#get-canceled-orders)