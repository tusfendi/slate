# Storefront & Privor
## Get Orders
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "payment_id": 470,
      "shop_id": 7,
      "nominal_invoice": 150000,
      "nominal_unique": 29,
      "nominal_transfer": 150000,
      "is_installment": false,
      "payment_from": "Storefront",
      "payment_status": "Confirmed Pay",
      "payment_type": 1,
      "payment_fee": null,
      "pg_provider": null,
      "xendit_id": null,
      "va_no": null,
      "created_by": 18550992,
      "updated_by": null,
      "created_at": "2020-06-22 00:19:05",
      "updated_at": null,
      "confirmed_at": "2020-06-22 00:19:05",
      "expired_at": "2020-06-23 00:19:05",
      "old_payment_id": null,
      "description": "",
      "customer": {
        "id": 18550992,
        "name": "Rahmat Rdn",
        "phone": "082244213171"
      },
      "bank": {
        "id": "18389",
        "name": "Saldo OrderPay"
      },
      "payment_status_code": 3,
      "orders": [
        {
          "po_number": "287",
          "order_id": "350"
        }
      ],
      "products": [
        {
          "name": "Ipit ",
          "quantity": 1,
          "product_meta_id": "7978133",
          "product_id": "1036"
        }
      ]
    },
    {
      "payment_id": 467,
      "shop_id": 7,
      "nominal_invoice": 232002,
      "nominal_unique": 16,
      "nominal_transfer": null,
      "is_installment": false,
      "payment_from": "Storefront",
      "payment_status": "Waiting for Payment",
      "payment_type": 1,
      "payment_fee": null,
      "pg_provider": null,
      "xendit_id": null,
      "va_no": null,
      "created_by": 18550992,
      "updated_by": null,
      "created_at": "2020-06-19 02:29:31",
      "updated_at": "2020-06-24 10:18:08",
      "confirmed_at": null,
      "expired_at": "2020-06-25 10:18:08",
      "old_payment_id": null,
      "description": "",
      "customer": {
        "id": 18550992,
        "name": "Rahmat Rdn",
        "phone": "082244213171"
      },
      "bank": {
        "id": "6624",
        "name": "Mandiri"
      },
      "payment_status_code": 4,
      "orders": [
        {
          "po_number": "280",
          "order_id": "343"
        }
      ],
      "products": [
        {
          "name": "Macbook Pro 2020 X ",
          "quantity": 2,
          "product_meta_id": "12",
          "product_id": "7"
        }
      ]
    }
  ],
  "meta": {
    "pagination": {
      "total": 81,
      "count": 2,
      "per_page": 2,
      "current_page": 21,
      "total_pages": 41,
      "links": {
        "previous": "https://api.ngorder.id/api/open/order/unconfirmed-privor?per_page=2&pagination_offset=20",
        "next": "https://api.ngorder.id/api/open/order/unconfirmed-privor?per_page=2&pagination_offset=22"
      }
    }
  }
}
```
Get unconfirmed Privor and Storefront orders.

### Endpoint
`GET https://api.ngorder.id/api/open/order/unconfirmed-privor`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Keyword to look for. It can be customer name or PO number
customer_category `(optional)` | integer | Customer category. Available values: `MEMBER` or `GUEST`
payment_status `(optional)` | integer | Payment status. Available values: `UNPAID`, `CONFIRM` or `ALL`. Default value: `CONFIRM`
per_page `(optional)` | integer | Data per page. Default value: `10`. Max `50`
pagination_offset `(optional)` | integer | Page number. Default value: `1`




## Get Detailed Order
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "payment_id": 513,
    "bill_total": 166001,
    "unique_code ": 0,
    "transfer_total": 166001,
    "payment_date": "2020-07-16 13:20:18",
    "holder_name": null,
    "pg_provider": "saldo",
    "is_manual_payment": "N",
    "bank": {
      "id": 18389,
      "bank": "Saldo OrderPay",
      "holder_name": null,
      "bank_number": null,
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/order.png"
    },
    "transfer_image": null,
    "note": null,
    "paid_at": "2020-07-16 13:20:18",
    "confirmation_status": true,
    "payment_status_code": 3,
    "payment_status": "Confirmed Pay",
    "is_installment": false,
    "installment_transferred": null,
    "payment_fee": 0,
    "virtual_account": null,
    "is_xendit_pay": true,
    "xendit_message": "An order rejection will be subject to an admin fee of IDR 5,500 for a refund to the customer",
    "orders": [
      {
        "order_id": 441,
        "po_number": 382,
        "note": "",
        "reseller": "Rahmat Rdn",
        "is_dropshipper": false,
        "dropshipper": {
          "name": null,
          "phone": null
        },
        "customer": {
          "name": "Rahmat Rdn",
          "address": "Jebus, Kabupaten Bangka Barat, Bangka Belitung",
          "phone": "082244213171"
        },
        "products": [
          "Macbook Pro 2020 X  X 1"
        ],
        "total_amount": 166001,
        "is_warehouse": false,
        "warehouse_name": null,
        "shipping_id": "3",
        "shipping_rate": "OKE",
        "shipping_logistic": "JNE",
        "shipping_cost": 56000,
        "shipping_logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/jne.png"
      }
    ]
  }
}
```
Get detailed privor order.

### Endpoint
`GET https://api.ngorder.id/api/open/order/unconfirmed-privor/{payment_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
payment_id | integer | Payment ID taken from [Get Privor Orders](#get-orders-2)






## Order Confirmation
> Example request:

```json
```

> Example response:

```json
{
  "id": 1234,
  "orders": [
    {
      "id": 5903,
      "action": "ACCEPT"
    },
    {
      "id": 5904,
      "action": "REJECT"
    }
  ]
}
```
Confirm privor orders.

### Endpoint
`PATCH https://api.ngorder.id/api/open/order/confirm`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Payment ID taken from [Get Privor Orders](#get-orders-2)
orders | array | Privor orders <table><tr><th>Key</th><th>Value</th></tr><tr><td>id</td><td>`integer` Privor order ID</td></tr><tr><td>action</td><td>`string` Confirmation action. Available values: `ACCEPT` or `REJECT`</td></tr></table>