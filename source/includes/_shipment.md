# Shipment
## Resend Package
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "The package has been successfully returned to the menu ready to be shipped",
  "data": {
    "id": "39384711"
  }
}
```
Take order back to status __ready to ship__.
### Endpoint
`POST https://api.ngorder.id/api/open/shipping/resend/{order_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
order_id | integer | Order ID taken from [Get Orders](#get-orders)







## Pickup Request
> Example request:

```json
{
  "pickup_request": [
    {
      "id": 122,
      "service": "DROP_OFF"
    },
    {
      "id": 123,
      "service": "PICKUP"
    }
  ]
}
```

> Example response:

```json
{
  "response": "sukses",
  "message": "1 paket berhasil diproses PICKREQ",
  "success_data": [
    1234567
  ],
  "status": "PICKUP_REQUEST"
}
```
Package pickup request.

### Endpoint
`POST https://api.ngorder.id/api/open/shipping/pickup-request`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
pickup_request | array | Order data <table><tr><th>Key</th><th>Value</th></tr><tr><td>id</td><td>`integer` Order ID taken from [Get Orders](#get-orders)</td></tr><tr><td>service `(optional)`</td><td>`string` Shipment service. Available values: `PICKUP` or `DROP_OFF`. Default value: `PICKUP`</td></tr></table>





## Cancel Pickup Request
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "Pickreq canceled successfully!",
  "data": 39384708
}
```
Cancel a pickup request.

### Endpoint
`POST https://api.ngorder.id/api/open/shipping/cancel-pickup`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID taken from [Get Orders](#get-orders)
reason `(optional)` | string | Reason for cancelling the pickup request. Required if courier vendor is JNE






## Get Active COD Couriers
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "expedition_name": "sicepat",
      "logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/sicepat.png"
    },
    {
      "expedition_name": "sap",
      "logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/sap.png"
    },
    {
      "expedition_name": "jne",
      "logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/jne.png"
    },
    {
      "expedition_name": "shipper",
      "logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/shipper.png"
    }
  ]
}
```
Get list of courier enabled for COD.
### Endpoint
`GET https://api.ngorder.id/api/open/shipping/cod-active`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token






## Get Shipment Invoices
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "id": "abcDEF",
      "date": "2021-01-21T20:06:03.000000Z",
      "vendor": "SICEPAT",
      "invoice_number": "INV-S-7-2021010007",
      "total": "Rp72.720",
      "status": "PENDING"
    },
    {
      "id": "abcXYZ",
      "date": "2020-10-01T01:49:27.000000Z",
      "vendor": "SICEPAT",
      "invoice_number": "INV-S-7-2020100005",
      "total": "Rp72.720",
      "status": "PENDING"
    }
  ],
  "meta": {
    "pagination": {
      "total": 7,
      "count": 2,
      "per_page": 2,
      "current_page": 1,
      "total_pages": 4,
      "links": {
        "next": "https://api.ngorder.id/api/open/shipping/invoice?pagination_offset=2"
      }
    }
  }
}
```
Get shipment invoices.
### Endpoint
`GET https://api.ngorder.id/api/open/shipping/invoice`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
courier `(optional)` | string | Expedition name taken from [Get Active COD Couriers](#get-active-cod-couriers)
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
status `(optional)` | string | Invoice status. Available values: `COMPLETE` or `PENDING`
per_page `(optional)` | integer | Data per page. Default value: `10`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default value: `1`







## Get Shipping Report
> Example request:

```json
```

> Example response:

```json
```
Get shipping report.
### Endpoint
`GET https://api.ngorder.id/api/open/shipping/report`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
courier `(optional)` | string | Expedition name taken from [Get Active COD Couriers](#get-active-cod-couriers)
interval `(optional)` | integer | Date range. Max 31 days. Default value: `7`







## Download Shipping Report
> Example request:

```json
```

> Example response:

```json
```
Download shipping report as CSV.
### Endpoint
`GET https://api.ngorder.id/api/open/shipping/report/download`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
courier `(optional)` | string | Expedition name taken from [Get Active COD Couriers](#get-active-cod-couriers)
interval `(optional)` | integer | Date range. Max 31 days. Default value: `7`






## Download Invoices as CSV
> Example request:

```json
```

> Example response:

```json
```
Download invoice as CSV file.
### Endpoint
`GET https://api.ngorder.id/api/open/shipping/invoice/download/csv/{id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Invoice ID taken from [Get Shipment Invoices](#get-shipment-invoices)







## Download Invoices as PDF
> Example request:

```json
```

> Example response:

```json
```
Download shipping invoice as PDF file.

### Endpoint
`GET https://api.ngorder.id/api/open/shipping/invoice/download/pdf/{invoice_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
invoice_id | string | Invoice ID taken from [Get Shipment Invoices](#get-shipment-invoices)







## Shipping Payments
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "date": "2021-01-27T18:44:08.000000Z",
      "vendor": "SICEPAT",
      "invoice_number": null,
      "description": "COD Reconsiliation 22 Jan 2021 - 29 Jan 2021",
      "total": "Rp7800",
      "status": "PENDING"
    }
  ],
  "meta": {
    "pagination": {
      "total": 8,
      "count": 1,
      "per_page": 1,
      "current_page": 1,
      "total_pages": 8,
      "links": {
        "next": "https://api.ngorder.id/api/open/shipping/payment?pagination_offset=2"
      }
    }
  },
  "withdrawable_balance": "Rp9.693.125"
}
```
Get shipping payment list.

### Endpoint
`GET https://api.ngorder.id/api/open/shipping/payment`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
courier `(optional)` | string | Expedition name taken from [Get Active COD Couriers](#get-active-cod-couriers)
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
status `(optional)` | string | Invoice status. Available values: `COMPLETE` or `PENDING`
per_page `(optional)` | integer | Data per page. Default value: `100`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default value: `1`







## Get Orders List
> Example request:

```json
```

> Example response:

```json
{
  "message": "",
  "min_pickup": 0,
  "min_drop_off": 0,
  "is_cancel_requirement": false,
  "data": [
    {
      "order_id": 510,
      "order_date": "2021-01-06",
      "request_date": null,
      "po_number": 450,
      "supplier": {
        "name": "Macbook Shop!",
        "address": "jalan bondowoso",
        "location": "Ranca Bali, Kabupaten Bandung",
        "code": "BDO",
        "phone": "0822442123123"
      },
      "customer": {
        "name": "TUsfendi",
        "address": "tes",
        "district": "SRONO",
        "city": "BANYUWANGI",
        "postal_code": "JBR20114"
      },
      "expedition": {
        "logistic_name": "JNE",
        "rate_name": "OKE",
        "is_cod": false,
        "cod_amount": 0,
        "awb_number": ""
      },
      "service": {
        "pickup": true,
        "drop_off": true
      },
      "dropship": []
    }
  ],
  "meta": {
    "pagination": {
      "total": 5,
      "count": 1,
      "per_page": 1,
      "current_page": 1,
      "total_pages": 5,
      "links": {
        "next": "https://api.ngorder.id/api/open/shipping?courier=jne&start_date=2020-11-06&end_date=2021-02-15&per_page=1&pagination_offset=2"
      }
    }
  }
}
```
Get list of orders in shipment.

### Endpoint
`GET https://api.ngorder.id/api/open/shipping`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Keyword to look for
courier `(optional)` | string | Expedition name taken from [Get Active COD Couriers](#get-active-cod-couriers)
status `(optional)` | string | Order progress. Available values: `READY_TO_SHIP`, `PICKUP_REQUEST`, `UNPICK`, `ON_PROCESS`, `DELIVERED`, `RETURNED`, `LOST`, `INVALID`, `SHIPMENT_PROBLEM` or `DROPOFF`. Default value: `READY_TO_SHIP`
type `(optional)` | string | Filter by type. Available values: `ORDER_ID`, `CUSTOMER_NAME` or `AWB_NUMBER`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`. Default value: today
cod_status `(optional)` | string | Shipment COD status. Available values: `NON_COD` or `COD`
supplier_id `optional` | integer | Supplier ID taken from [Get Suppliers](#get-suppliers)
per_page `(optional)` | integer | Data per page. Default value: `50`
pagination_offset `(optional)` | integer | Page number. Default value: `1`








## Download Order Shipping
> Example request:

```json
```

> Example response:

```json
```
Download list of orders in shipment as Excel file.

### Endpoint
`GET https://api.ngorder.id/api/open/shipping/download`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Keyword to look for
courier `(optional)` | string | Expedition name taken from [Get Active COD Couriers](#get-active-cod-couriers)
status `(optional)` | string | Order progress. Available values: `READY_TO_SHIP`, `PICKUP_REQUEST`, `UNPICK`, `ON_PROCESS`, `DELIVERED`, `RETURNED`, `LOST`, `INVALID`, `SHIPMENT_PROBLEM` or `DROPOFF`. Default value: `READY_TO_SHIP`
type `(optional)` | string | Filter by type. Available values: `ORDER_ID`, `CUSTOMER_NAME` or `AWB_NUMBER`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`. Default value: today
cod_status `(optional)` | string | Shipment COD status. Available values: `NON_COD` or `COD`
supplier_id `optional` | integer | Supplier ID taken from [Get Suppliers](#get-suppliers)








## Remove Order
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "Package removed successfully",
  "data": {
    "id": "39384759"
  }
}
```
Remove order from shipment list.

### Endpoint
`DELETE https://api.ngorder.id/api/open/shipping/remove/{order_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
order_id | integer | Order ID taken from [Get Orders](#get-orders)