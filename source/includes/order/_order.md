# Order
## Get Wholesale Price
> Example request:

```json
```
> Example response:

```json
{
  "response": "success",
  "data": {
    "variation_id": 123,
    "quantity": "10",
    "price": 10000
  }
}
```
Get wholesale prices of selected product variant.

### Endpoint
`GET https://api.ngorder.id/api/open/order/wholesale`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
variation_id | integer | Product variant ID
qty | integer | Product quantity


## Get Price Access
> Example request:

```json
```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "wholesale_access": false,
    "discount_access": true
  }
}
```
Get customer category price access.

### Endpoint
`GET https://api.ngorder.id/api/open/order/check-price/{customer_category_code}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
customer_category_code | integer | Customer category ID

## Create Order
> Example request:

```json
`{
  "order_date": "2020-10-26",
  "customer_sender_id": 23101433,
  "customer_receiver_id": 23101441,
  "supplier_id": 17118,
  "order_source_id": null,
  "is_print": false,
  "products": [
    {
      "id": 7978133,
      "qty": 1,
      "product_status": "S",
      "warehouse_id": 26
    }
  ],
  "expedition": {
    "id": 349,
    "rate": 23000,
    "name": "SAP",
    "auto_pickup": false
  },
  "payment": {
    "status": "UNPAID",
    "date": "2020-10-26",
    "bank_id": 847
  },
  "order_cost": [
    {
      "name": "Ini Untuk biaya jurnal",
      "category": "OTHER COST",
      "type": "NOMINAL",
      "nominal": 1200
    },
    {
      "name": "Diskon persen",
      "category": "DISCOUNT",
      "type": "PERCENTAGE",
      "percentage": 2
    },
    {
      "name": "Geni Biru",
      "category": "DISCOUNT",
      "type": "NOMINAL",
      "nominal": 3000
    },
    {
      "name": "Pecah Belah",
      "category": "INSURANCE",
      "type": "NOMINAL",
      "nominal": 2000
    }
  ],
  "source": "MOBILE"
}
```
> Example success response:

```json
{
  "request_id": "5f967ba06a030",
  "response": "Success",
  "message": "Order created",
  "data": {
    "order_id": 123,
    "po_number": 10
  }
}
```

> Example error response:

```json
{
  "request_id": "5f967c71a9cab",
  "response": "Failed",
  "message": {
    "payment.cost_of_goods_sales": [
      "The payment.cost of goods sales field is required when products.0.product_status is R."
    ],
    "products.0.product_status": [
      "The products.0.product_status must be one of the following value : S"
    ]
  },
  "data": null
}
```

Create an order.

### Endpoint
`POST https://api.ngorder.id/api/open/order`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
customer_sender_id | integer |  Customer sender ID taken from [Customer](#customer)
customer_receiver_id | integer | Customer receiver ID taken from [Customer](#customer)
supplier_id | integer | Supplier ID taken from [Supplier](#supplier)
order_date | string | Order date. Format `yyyy-mm-dd`
order_source_id `(optional)` | integer | Order source ID taken from [Order Source](#order-source)
note `(optional)` | string | Note for the order
is_print | boolean | Order print status
products | array | Product variants detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>id</td><td>`integer` Product variant ID</td></tr><tr><td>qty</td><td>`integer` Product quantity</td></tr><tr><td>warehouse_id `(optional)`</td><td>`integer` Product variant warehouse ID taken from [Get Warehouses](#get-warehouses)</td></tr><tr><td>product_status</td><td>`string` Product stock type `S` (own stock), `R` (from other suppliers) or `PO` (preorder)</td></tr><tr><td>type `(optional)`</td><td>`string` Product discount type. Available values: `NOMINAL` or `PERCENTAGE`</td></tr><tr><td>percentage `(optional)`</td><td>`integer` Discount percentage. Required if `type: PERCENTAGE`</td></tr><tr><td>nominal `(optional)`</td><td>`integer` Discount nominal. Required if `type: NOMINAL`</td></tr><tr><td>flag `(optional)`</td><td>`string` Product update status. Available values: `EDIT`, `NEW` or `DELETE`</td></tr><tr><td>discount_promo `(optional)`</td><td>`integer` Product promo discount nominal. If this filled product discount will be removed</td></tr><tr><td>promo_id `(optional)`</td><td>`integer` Promo ID</td></tr></table>
expedition | array | Expedition detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>id</td><td>`integer` Expedition ID</td></tr><tr><td>rate</td><td>`integer` Expedition cost</td></tr><tr><td>name</td><td>`string` Expedition name</td></tr><tr><td>auto_pickup</td><td>`boolean` Expedition auto pickup status</td></tr><tr><td>discount_promo `(optional)`</td><td>`integer` Expedition discount nominal</td></tr><tr><td>promo `(optional)`</td><td>`array` Promo detail from [Product Variants](#get-product-variations)</td></tr></table>
payment | array | Payment detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>status</td><td>`string` Payment status. Available values: `PAID`, `INSTALLMENT` or `UNPAID`</td></tr><tr><td> date `(optional)` </td><td>`string` Payment date. Required if `status: PAID or INSTALLMENT`. Format `yyy-mm-dd`</td></tr><tr><td>bank_id `(optional)` </td><td>`integer` Bank ID. Required if `status: PAID or INSTALLMENT` taken from [Bank Accounts](#get-shop-bank-accounts)</td></tr><tr><td>amount</td><td>`integer` Payment amount. Required if `status: PAID or INSTALLMENT`</td></tr><tr><td>cost_of_goods_sales `(optional)` </td><td>`integer` Cost to be paid to the supplier. Required if `product_status: R` (see [Create a Product](#create-product))</td></tr></table>
order_cost `(optional)` | array | Other cost detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>name</td><td>`string` Order cost name</td></tr><tr><td>category</td><td>`string` Cost category. Available values: `DISCOUNT`, `OTHER COST` or `INSURANCE`</td></tr><tr><td>type</td><td>`string` Cost type. Available values: `NOMINAL` or `PERCENTAGE`</td></tr><tr><td>percentage `(optional)` </td><td>`integer` Order cost percentage. Required if `type: PERCENTAGE`</td></tr><tr><td>nominal `(optional)` </td><td>`integer` Order cost nominal. Required if `type: NOMINAL`</td></tr></table>
awb_number `(optional)` | string | Air waybill number
send_sms `(optional)` | boolean | SMS status. Default value: `false`
marketplace_awb `(optional)` | string | Marketplace air waybill
source | string | Source platform. Available values: `MOBILE` or `WEB`


## Add AWB Number
> Example request:

```json
```

> Example response:

```json
{
  "request_id": "5fab8035eabd9",
  "response": "Success",
  "message": "Awb number has been updated",
  "data": {
    "order_id": 123,
    "po_number": 10,
    "notification": {
      "id": 1,
      "title": "Notification successfully sent",
      "content": "Your receipt credit notification currently has 968350 remaining"
    }
  }
}
```
Add AWB number for created order.

### Endpoint
`POST https://api.ngorder.id/api/open/order/awb-number/add`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID taken from [Create Order](#create-order) success response
awb_number | string | Airway bill


## Get Orders
> Example request:

```json
```
> Example response:

```json
{
  "data": [
    {
      "order_id": 1115,
      "po_number": 10576,
      "shop_id": 7,
      "order_date": "2020-10-08",
      "sender_name": "Tusfendi",
      "sender_address": "srono",
      "receiver_name": "Tusfendi",
      "receiver_address": "srono",
      "total_amount": 141000,
      "shipping_rate": "REGPACK",
      "shipping_logistic": "Lion Parcel",
      "weight": 1,
      "note": "",
      "origin_name": "A Supplier 1",
      "origin_address": "jalan bondowoso",
      "cost_of_goods_sold": 100000,
      "order_source": "",
      "other_cost_amount": 0,
      "order_progress_status": "NO AWB",
      "order_status": "ACCEPTED",
      "order_category": "APP",
      "payment_status": "PAID",
      "payment_date": "2020-10-08",
      "products": [
        {
          "product_meta_id": 7978133,
          "name": "Ipit",
          "price": 0,
          "quantity": 1
        }
      ],
      "shopee": null,
      "created_by_name": "Juragan",
      "created_at": "2020-10-08 09:26:45",
      "updated_by_name": "Juragan",
      "updated_at": "2020-10-08 09:26:45",
      "awb_number": ""
    },
    {
      "order_id": 1114,
      "po_number": 10575,
      "shop_id": 7,
      "order_date": "2020-10-06",
      "sender_name": "Tusfendi",
      "sender_address": "srono",
      "receiver_name": "Tusfendi",
      "receiver_address": "srono",
      "total_amount": 304000,
      "shipping_rate": "REG",
      "shipping_logistic": "SiCepat",
      "weight": 2,
      "note": "",
      "origin_name": "A Supplier 1",
      "origin_address": "jalan bondowoso",
      "cost_of_goods_sold": -64000,
      "order_source": "",
      "other_cost_amount": 0,
      "order_progress_status": "UNPAID",
      "order_status": "ACCEPTED",
      "order_category": "APP",
      "payment_status": "UNPAID",
      "payment_date": null,
      "products": [
        {
          "product_meta_id": 7978133,
          "name": "Sandal",
          "price": 10000,
          "quantity": 2
        }
      ],
      "shopee": null,
      "created_by_name": "Juragan",
      "created_at": "2020-10-06 16:10:02",
      "updated_by_name": "Juragan",
      "updated_at": "2020-10-06 16:10:02",
      "awb_number": null
    }
  ],
  "meta": {
    "pagination": {
      "total": 176,
      "count": 10,
      "per_page": 10,
      "current_page": 1,
      "total_pages": 18,
      "links": {
        "next": "https://api.ngorder.id/api/open/order?pagination_offset=2"
      }
    }
  }
}
```
Get all data.

### Endpoint
`GET https://api.ngorder.id/api/open/order`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Keyword to look for
payment_status `(optional)` | string | Filter by payment status. Available values: `UNPAID`, `PAID` or `INSTALLMENT`
order_progress_status | string | Filter by order progress status. Available values: `UNPAID`, `NO AWB`, `ON PROCESS`, `DELIVERED`, `UNPROCESSED` or `INSTALLMENT`
order_category `(optional)` | string | Source of created order. Available values: `APP`, `PRIVOR`, `STORE_FRONT`, `SHOPEE`, `QUICK_ORDER` or `UNCATEGORIZED`
order_source_id `(optional)` | integer | Sales channel ID taken from [Order Source](#get-order-sources)
type `(optional)` | string | Order type. Available values: `ORDER_ID`, `CUSTOMER_NAME`, `AWB_NUMBER`, `CUSTOMER_PHONE`, `SHOPEE_INVOICE`, `PRODUCT_NAME`, `SKU` or `SHIPPER_TRACKING`
order_by `(optional)` | string | Order the data. Available values: `ORDER_DATE` or `PAYMENT_DATE`. Default value: `ORDER_DATE`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`. Default value: 30 days ago
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`. Default value: today
user_id `(optional)` | integer | The ID of admin who made this order
bank_id `(optional)` | integer | Bank ID taken from [Bank Accounts](#get-shop-bank-accounts)
warehouse_id  `(optional)` |  integer | Product variant warehouse ID taken from [Get Warehouses](#get-warehouses)
customer_category_code `(optional)` | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](#get-categories-2)
expedition_id `(optional)` | integer | Expedition ID. Available values: `1` (JNE), `2` (TIKI), `3` (POS), `4` (SICEPAT), `5` (WAHANA), `6` (JNT Express), `7` (Alfatrex), `8` (Lion Parcel), `9` (Ninja Xpress), `10` (SAP), `11` (RPX), `98` (pickup at shop) or `99` (manual input)
pickup `(optional)` | integer | Pickup status. Available values: `0` (ready to send), `1` (pickup request) or `2` (delivered)
print_status `(optional)` | string | Print status. Available value: `Y` or `N`
product_type `(optional)` | string | Product stock type. `S` (own stock), `R` (from other suppliers) or `PO` (preorder)
per_page `(optional)` | integer | Data per page. Default `10`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default `1`




## Get Orders Detail
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "_id": "5ef0740130b2667b424d16fe",
      "order_id": 34481623,
      "po_number": 43295,
      "shop_id": 35548,
      "order_date": "2020-06-21",
      "customer": {
        "id": 23726458,
        "name": "Windira Aliyani",
        "phone": "08123456789",
        "district": "Batununggal",
        "city": "Kota Bandung",
        "province": "Jawa Barat",
        "district_id": 346,
        "city_id": 23,
        "province_id": 9,
        "postal_code": "40274",
        "address": "Jl. abc, KOTA BANDUNG, BATUNUNGGAL, JAWA BARAT, ID, 40274",
        "line": null,
        "email": null,
        "type": "Pelanggan"
      },
      "dropshipper": null,
      "receiver": {
        "id": 23726458,
        "name": "Windira Aliyani",
        "phone": "08123456789",
        "district": "Batununggal",
        "city": "Kota Bandung",
        "province": "Jawa Barat",
        "district_id": 346,
        "city_id": 23,
        "province_id": 9,
        "postal_code": "40274",
        "address": "Jl. abc, KOTA BANDUNG, BATUNUNGGAL, JAWA BARAT, ID, 40274",
        "line": null,
        "email": null,
        "type": "Pelanggan"
      },
      "total_amount": 110376,
      "shipping": {
        "id": "57",
        "rate_name": "EZ",
        "logistic_name": "J&T",
        "cost": 2000
      },
      "weight": 0.4,
      "note": "",
      "origin": {
        "id": 20241,
        "name": "Myjivi WH",
        "location": "Cisarua, Kabupaten Bandung Barat",
        "phone": "0812345789",
        "address": "jl. abc ",
        "note": "Myjivi WH",
        "is_shipper_active": "semua dari sini",
        "city_id": 24
      },
      "payment": {
        "payment_histoy": [
          {
            "id": 2112307,
            "payment_id": null,
            "order_id": 34481623,
            "description": "Pembayaran Order PO#43295 dari Shopee",
            "nominal": 110376,
            "payment_fee": null,
            "bank": {
              "origin": {
                "id": null,
                "account_name": null,
                "account_number": null,
                "transfer_image": null
              },
              "destination": {
                "id": 27410,
                "bank_name": "Shopee"
              }
            },
            "note": null,
            "pg_provider": "Shopee",
            "va_no": null,
            "is_confirmed": 1,
            "type": 11,
            "is_installment_first": null,
            "created_by": 50468,
            "updated_by": null,
            "paid_at": {
              "$date": {
                "$numberLong": "1592816651000"
              }
            }
          }
        ]
      },
      "cost_of_goods_sold": null,
      "order_source": null,
      "order_cost": [
        {
          "category": "DISCOUNT",
          "description": "Coins",
          "nominal": 1524,
          "percentage": 0,
          "is_percentage": false
        },
        {
          "category": "OTHER COST",
          "description": "Buyer Paid Shipping Fee",
          "nominal": 2000,
          "percentage": 0,
          "is_percentage": false
        },
        {
          "category": "ESCROW PLUS",
          "description": "Buyer Total Amount",
          "nominal": 110376,
          "percentage": 0,
          "is_percentage": false
        },
        {
          "category": "ESCROW PLUS",
          "description": "Coins",
          "nominal": 1524,
          "percentage": 0,
          "is_percentage": false
        },
        {
          "category": "ESCROW MINUS",
          "description": "Commission Fee",
          "nominal": 1099,
          "percentage": 0,
          "is_percentage": false
        },
        {
          "category": "ESCROW MINUS",
          "description": "Service Fee",
          "nominal": 2748,
          "percentage": 0,
          "is_percentage": false
        },
        {
          "category": "ESCROW PLUS",
          "description": "Final Shipping Fee",
          "nominal": -1400,
          "percentage": 0,
          "is_percentage": false
        }
      ],
      "awb": {
        "update_at": {
          "$date": {
            "$numberLong": "1592887575675"
          }
        },
        "number": "JP8507716855"
      },
      "discount_amount": null,
      "order_cost_amount": null,
      "coupon": null,
      "is_printed": false,
      "is_shipper_order": false,
      "is_note_print": true,
      "order_progress_status": "DELIVERED",
      "order_status": "ACCEPT",
      "order_category": "SHOPEE",
      "payment_status": "PAID",
      "is_private_order": false,
      "payment_date": "2020-06-22",
      "products": [
        {
          "product_meta_id": 7950476,
          "name": "Rengganis Midi Dress Combed",
          "category": {
            "id": 40088,
            "name": ""
          },
          "description": "<p>Rengganis Midi Dress Combed</p>",
          "product_status": "S",
          "price": "109900",
          "cost_of_goods_sold": "85000",
          "quantity": "1",
          "discount_nominal": "1",
          "discount_percentage": 0,
          "is_warehouse": false
        }
      ],
      "shopee": {
        "ordersn": "200622F0D69C9G",
        "buyer_username": "windiraaliyani",
        "total_escrow": "106653",
        "total_amount": "110376",
        "status": "COMPLETED",
        "payment_method": "Shopee Wallet V2"
      },
      "created_by": {
        "id": 50468,
        "name": "Vhenny pratiwie",
        "email": "v8@gmail.com"
      },
      "updated_by": {
        "id": 50468,
        "name": "Vhenny pratiwie",
        "email": "v8@gmail.com"
      },
      "updated_at": "2020-06-23T04:46:15.755000Z",
      "created_at": "2020-06-22T09:04:01.919000Z"
    }
  ],
  "meta": {
    "pagination": {
      "total": 3230,
      "count": 1,
      "per_page": 1,
      "current_page": 1,
      "total_pages": 3230,
      "links": {
        "next": "https://api.ngorder.id/api/order?pagination_offset=2"
      }
    }
  }
}
```
Get list of orders detail

### Endpoint
`GET https://api.ngorder.id/api/open/order/details`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
order_status `(optional)` | string | Order status. Available values: `ACCEPTED` or `REJECTED`
payment_status `(optional)` | string | Order payment status. Available values: `UNPAID`, `PAID`, `FAIL`, `WAITING_CONFIRMATION`, `WAITING PAYMENT`, `REFUND_REJECTED` or `EXPIRED`
order_progress_status `(optional)` | Order progress status. Available status: `UNPAID`, `NO AWB`, `ON PROCESS` or `DELIVERED`
order_category `(optional)` | string | Source of created order. Available values: `APP`, `PRIVOR`, `SF_MEMBER`, `SF_GUEST` or `SHOPEE`
create_from `(optional)` | string | Date from which orders are created. Format `yyyy-mm-dd`
create_to `(optional)` | string | Date to which orders are created. Format `yyyy-mm-dd`
per_page `(optional)` | integer | Data per page. Default `10`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default `1`



<!-- 
## Get Single Order Detail
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "order_id": 1352,
    "po_number": 123,
    "shop_id": 7,
    "order_date": "2020-11-19 00:00:00",
    "sender": {
      "id": 23101432,
      "name": "Tusfendi",
      "phone": "082336440033",
      "address": "srono",
      "postal_code": "68471",
      "district_id": 620,
      "district": "Srono",
      "city_id": 42,
      "city": "Kabupaten Banyuwangi",
      "province_id": 11,
      "province": "Jawa Timur",
      "region": "Srono, Kabupaten Banyuwangi, Jawa Timur",
      "email": "tusfendi@gmail.com",
      "line": "",
      "other": null,
      "category_code": "N",
      "category": "PELANGGAN"
    },
    "receiver": {
      "id": 23101432,
      "name": "Tusfendi",
      "phone": "082336440033",
      "address": "srono",
      "postal_code": "68471",
      "district_id": 620,
      "district": "Srono",
      "city_id": 42,
      "city": "Kabupaten Banyuwangi",
      "province_id": 11,
      "province": "Jawa Timur",
      "region": "Srono, Kabupaten Banyuwangi, Jawa Timur",
      "email": "tusfendi@gmail.com",
      "line": "",
      "other": null,
      "category": ""
    },
    "total_amount": 24000,
    "remaining_amount": 0,
    "shipping_id": 99,
    "shipping_rate": "",
    "shipping_logistic": "Tus",
    "shipping_cost": 2000,
    "weight": 0.4,
    "note": "",
    "order_source": "",
    "other_cost_amount": 20000,
    "order_progress_status": "NO AWB",
    "order_status": "ACCEPTED",
    "order_category": "APP",
    "payment_status": "PAID",
    "payment_date": "2020-11-19",
    "shopee": null,
    "created_by_name": "Owner Ngorders",
    "created_at": "2020-11-19 08:29:15",
    "updated_by_name": "Owner Ngorders",
    "updated_at": "2020-11-19 08:29:15",
    "awb_number": "",
    "product_status": "S",
    "cost_of_goods_sales": 0,
    "order_cost": [
      {
        "name": "Disko yen",
        "category": "DISCOUNT",
        "nominal": 2000,
        "percentage": 0,
        "type": "NOMINAL"
      },
      {
        "name": "Ini Untuk biaya jurnal",
        "category": "OTHER COST",
        "nominal": 20000,
        "percentage": 0,
        "type": "NOMINAL"
      }
    ],
    "origin": {
      "id": 17114,
      "name": "A Supplier 1",
      "location": "Ranca Bali, Kabupaten Bandung",
      "phone": "0822442123123",
      "address": "jalan bondowoso",
      "note": "heuheu",
      "is_shipper_active": true,
      "city_id": 22
    },
    "order_detail": [
      {
        "variation_id": 8055898,
        "qty": 2,
        "price": 2000,
        "warehouse_id": 38,
        "warehouse_stock_id": 28,
        "type": null,
        "nominal": 0,
        "percentage": 0,
        "variation_detail": {
          "variation_id": 8055898,
          "product_id": 1244,
          "name": "dari sby ya",
          "product_type": "S",
          "publish_status": "Y",
          "stock_quantity": 50,
          "sku": "P039V01",
          "image": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
          "thumbnail": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
          "discount": 0,
          "color": "",
          "size": "",
          "weight": 200,
          "category_id": 0,
          "created_at": "2020-11-19T08:27:36+07:00",
          "price": 2000,
          "price1": 2000,
          "price2": 2000,
          "price3": 2000,
          "price_reseller": 2000,
          "price_buy": 200,
          "wholesale_status": "Y",
          "is_warehouse": 1,
          "warehouse_stock": [
            {
              "id_warehouse": 4,
              "stock": 30,
              "warehouse_name": "Gudang 2 Medan",
              "supplier_id": 2790
            },
            {
              "id_warehouse": 38,
              "stock": 18,
              "warehouse_name": "Jogja 2",
              "supplier_id": 17114
            }
          ]
        }
      }
    ]
  }
}
```
Get single order detail

### Endpoint
`GET https://api.ngorder.id/api/open/order/detail`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID -->









## Get Payment Histories
> Example request:

```json
```

> Example response:

```json
{
  "response": "success",
  "data": [
    {
      "payment_id": 1994,
      "bank_id": "847",
      "bank_name": "BCA",
      "account_number": "1234567789",
      "paid_at": "2020-11-23",
      "created_at": "2020-11-23 11:05:44",
      "nominal": "Rp100.000",
      "status": "INSTALLMENT"
    },
    {
      "payment_id": 1995,
      "bank_id": "847",
      "bank_name": "BCA",
      "account_number": "1234567789",
      "paid_at": "2020-11-23",
      "created_at": "2020-11-23 11:06:15",
      "nominal": "Rp126.947",
      "status": "PAID"
    }
  ]
}
```
Get order payment histories.

### Endpoint
`GET https://api.ngorder.id/api/open/order/payment-history`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID or Payment ID
status `(optional)` | string | Where to get the data. Available values: `ORDER` or `PAYMENT`. Default values: `ORDER`


## Get Admin Revenue
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "user_id": 5,
      "name": "Faizal",
      "level": "Owner",
      "net_sales": 150000,
      "gross_profit": 50000,
      "order_count": 2,
      "item_sold": 10
    },
    {
      "user_id": 0,
      "name": "Uncategorized",
      "level": "Admin",
      "net_sales": 84000,
      "gross_profit": 14000,
      "order_count": 1,
      "item_sold": 7
    }
  ]
}
```
Get revenue insights, items sold and total orders made by admin.

### Endpoint
`GET https://api.ngorder.id/api/open/order/admin-revenue`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`. Default values: start date of current month
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`. Default values: today

## Download
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "Success, your data will be sent to juragan@ngorder.id soon"
}
```
Download order data.

### Endpoint
`GET https://api.ngorder.id/api/open/order/download`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
payment_status `(optional)` | string | Order payment status. Available status: `UNPAID`, `PAID` or `INSTALLMENT`
order_progress_status `(optional)` | Order progress status. Available status: `UNPAID`, `NO AWB`, `ON PROCESS`, `DELIVERED`, `UNPROCESSED` or `INSTALLMENT`
order_category `(optional)` | string | Source of created order. Available values: `APP`, `PRIVOR`, `STORE_FRONT`, `SHOPEE`, `QUICK_ORDER` or `UNCATEGORIZED`
order_source_id `(optional)` | integer | Sales channel ID taken from [Order Source](#get-order-sources)
type `(optional)` | string | Filter type. Available values: `ORDER_ID`, `CUSTOMER_NAME`, `AWB_NUMBER`, `CUSTOMER_PHONE`, `SHOPEE_INVOICE`, `PRODUCT_NAME`, `SKU` or `SHIPPER_TRACKING`
keyword `(optional)` | string | Keyword to look for
order_by `(optional)` | string | Order the data. Available values: `ORDER_DATE` or `PAYMENT_DATE`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`. Default values: 30 days ago
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`. Default values: today
user_id `(optional)` | integer | User ID
bank_id `(optional)` | integer | Bank ID taken from [Bank Accounts](#get-shop-bank-accounts)
warehouse_id  `(optional)` |  integer | Product variant warehouse ID taken from [Get Warehouses](#get-warehouses)
customer_category_code `(optional)` | integer | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](#get-categories-2)
expedition_id `(optional)` | integer | Expedition ID. Available values: `1` (JNE), `2` (TIKI), `3` (POS), `4` (SICEPAT), `5` (WAHANA), `6` (JNT Express), `7` (Alfatrex), `8` (Lion Parcel), `9` (Ninja Xpress), `10` (SAP), `11` (RPX), `98` (pickup at shop) or `99` (manual input)
pickup `(optional)` | integer | Pickup status. Available values: `0` (ready to send), `1` (pickup request) or `2` (delivered)
print_status `(optional)` | string | Print status. Available value: `Y` or `N`
without_being_sent `(optional)` | boolean | Without being sent to email. Default value: `false`
per_page `(optional)` | integer | Data per page. Default `10`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default `1`


## Update Payment
> Example request:

```json
{
  "id": 1312,
  "payment": {
    "status": "INSTALLMENT",
    "amount": 100000,
    "date": "2020-11-09",
    "bank_id": 123
  }
}
```

> Example success response:

```json
{
  "request_id": "5fa8a55fcf9f0",
  "response": "success",
  "message": [
    "Payment Updated"
  ],
  "data": {
    "order_id": 1312,
    "po_number": 10709,
    "payment_status": "C"
  }
}
```

> Example error response:

```json
{
  "response": "Failed",
  "message": {
    "id": [
      "Order has been paid"
    ],
    "amount": [
      "Amount is more than amount remaining of this order"
    ],
    "maximum amount": [
      0
    ]
  },
  "data": null
}
```
Update order payment.

### Endpoint
`PATCH https://api.ngorder.id/api/open/order/quick-payment`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID taken from [Get Orders](#get-orders)
payment | array | Payment details <table><tr><th>Key</th><th>Value</th></tr><tr><td>status</td><td>`integer` Payment status. Available values: `PAID` or `INSTALLMENT`</td></tr><tr><td>date</td><td>`string` Payment date. Format `yyyy-mm-dd`</td></tr><tr><td>bank_id</td><td>`integer` Bank ID taken from [Bank Accounts](#get-shop-bank-accounts)</td></tr><tr><td>amount `(optional)`</td><td>`integer` Payment amount. Required if `status: INSTALLMENT`</td></tr><tr><td>cost_of_goods_sales</td><td>`integer` Cost to be paid to the supplier. Required if `product_status: R` (see [Create a Product](#create-product))</td></tr></table>


## Update Order
> Example request:

```json
```

> Example response:

```json
```
Update existing order.

### Endpoint
`PATCH https://api.ngorder.id/api/open/order`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
order_id | integer | Order ID taken from [Get Orders](#get-orders)
customer_sender_id | integer |  Customer sender ID taken from [Customer](#customer)
customer_receiver_id | integer | Customer receiver ID taken from [Customer](#customer)
supplier_id | integer | Supplier ID taken from [Supplier](#supplier)
order_source_id `(optional)` | integer | Order source ID taken from [Order Source](#order-source)
note `(optional)` | string | Note for the order
is_print | boolean | Order print status
products | array | Product variants detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>id</td><td>`integer` Product variant ID</td></tr><tr><td>qty</td><td>`integer` Product quantity</td></tr><tr><td>warehouse_id `(optional)`</td><td>`integer` Product variant warehouse ID taken from [Get Warehouses](#get-warehouses)</td></tr><tr><td>product_status</td><td>`string` Product stock type `S` (own stock), `R` (from other suppliers) or `PO` (preorder)</td></tr><tr><td>type `(optional)`</td><td>`string` Product discount type. Available values: `NOMINAL` or `PERCENTAGE`</td></tr><tr><td>percentage `(optional)`</td><td>`integer` Discount percentage. Required if `type: PERCENTAGE`</td></tr><tr><td>nominal `(optional)`</td><td>`integer` Discount nominal. Required if `type: NOMINAL`</td></tr><tr><td>flag `(optional)`</td><td>`string` Product update status. Available values: `EDIT`, `NEW` or `DELETE`</td></tr><tr><td>discount_promo `(optional)`</td><td>`integer` Product promo discount nominal. If this filled product discount will be removed</td></tr><tr><td>promo_id `(optional)`</td><td>`integer` Promo ID</td></tr></table>
expedition | array | Expedition detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>id</td><td>`integer` Expedition ID</td></tr><tr><td>rate</td><td>`integer` Expedition cost</td></tr><tr><td>name</td><td>`string` Expedition name</td></tr><tr><td>auto_pickup</td><td>`boolean` Expedition auto pickup status</td></tr><tr><td>discount_promo `(optional)`</td><td>`integer` Expedition discount nominal</td></tr><tr><td>promo `(optional)`</td><td>`array` Promo detail from [Product Variants](#get-product-variations)</td></tr></table>
payment | array | Payment detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>status</td><td>`string` Payment status. Available values: `PAID`, `INSTALLMENT` or `UNPAID`</td></tr><tr><td> date `(optional)` </td><td>`string` Payment date. Required if `status: PAID or INSTALLMENT`. Format `yyy-mm-dd`</td></tr><tr><td>bank_id `(optional)` </td><td>`integer` Bank ID. Required if `status: PAID or INSTALLMENT` taken from [Bank Accounts](#get-shop-bank-accounts)</td></tr><tr><td>amount</td><td>`integer` Payment amount. Required if `status: PAID or INSTALLMENT`</td></tr><tr><td>cost_of_goods_sales `(optional)` </td><td>`integer` Cost to be paid to the supplier. Required if `product_status: R` (see [Create a Product](#create-product))</td></tr></table>
order_cost `(optional)` | array | Other cost detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>name</td><td>`string` Order cost name</td></tr><tr><td>category</td><td>`string` Cost category. Available values: `DISCOUNT`, `OTHER COST` or `INSURANCE`</td></tr><tr><td>type</td><td>`string` Cost type. Available values: `NOMINAL` or `PERCENTAGE`</td></tr><tr><td>percentage `(optional)` </td><td>`integer` Order cost percentage. Required if `type: PERCENTAGE`</td></tr><tr><td>nominal `(optional)` </td><td>`integer` Order cost nominal. Required if `type: NOMINAL`</td></tr></table>
awb_number `(optional)` | string | Air waybill number
send_sms `(optional)` | boolean | SMS status. Default value: `false`
marketplace_awb `(optional)` | string | Marketplace air waybill
source | string | Source platform. Available values: `MOBILE` or `WEB`








## Delete Installment History
> Example request:

```json
```

> Example response:

```json
{
  "response": "success",
  "message": "Success, payment history has been deleted",
  "data": null
}
```
Delete installment payment history.

### Endpoint
`DELETE https://api.ngorder.id/api/open/order/installment/{order_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
order_id | integer | Order ID taken from [Get Orders](#get-orders)