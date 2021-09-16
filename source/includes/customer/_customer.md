# Customer
## Create Customer
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "customer_id": 123,
    "name": "Budi"
  }
}
```
Create a customer

### Endpoint
`POST https://api.ngorder.id/api/open/customer/create`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
name | string | Customer's name
phone | numeric | Customer's phone number
district_id | numeric | District ID taken from [Region](#region)
address | string | Customer's detailed address
postal_code `(optional)` | numeric | Postal code
category | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](#get-categories-2)
line `(optional)` | string | Customer's Line ID
email `(optional)` | string | Customer's email
other `(optional)` | string | Customer's other contacts
is_active | string | Customer's activation status. Available values: `Y` (active), `N`  (non-active), `R` (requested customer) or `T` (unactivated Storefront customer email)


## Privor Activation
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "message": "Successful run"
}
```
Activate or deactivate customer's Storefront account

### Endpoint
`POST https://api.ngorder.id/api/open/customer/privor-activation`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Customer's ID
active | boolean | Activation status
email | string | Customer's email
name `(optional)` | string | Customer's new name
phone `(optional)` | numeric | Customer's new phone number 


## Get Customers
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "id": 122,
      "name": "Angga",
      "name_initial": "A",
      "phone": "628212345678",
      "address": "Desa ABC ,KAB. TEGAL, DUKUHTURI, JAWA TENGAH, ID, 52192",
      "postal_code": "52192",
      "district": "Dukuhturi",
      "city": "Kabupaten Tegal",
      "province": "Jawa Tengah",
      "email": null,
      "line": null,
      "other": null,
      "category_code": "N",
      "category": "Pelanggan"
    },
    {
      "id": 123,
      "name": "Budi",
      "name_initial": "B",
      "phone": "628212345678",
      "address": "Jln. ABC ,KAB. BANJARNEGARA, MANDIRAJA, JAWA TENGAH, ID, 53473",
      "postal_code": "53473",
      "district": "Mandiraja",
      "city": "Kabupaten Banjarnegara",
      "province": "Jawa Tengah",
      "email": null,
      "line": null,
      "other": null,
      "category_code": "N",
      "category": "Pelanggan"
    }
  ],
  "meta": {
    "pagination": {
      "total": 100,
      "count": 2,
      "per_page": 2,
      "current_page": 1,
      "total_pages": 50,
      "links": {
        "next": "https://api.ngorder.id/api/customer?pagination_offset=2"
      }
    }
  }
}
```
Get customers

### Endpoint
`GET https://api.ngorder.id/api/open/customer`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Customer name to look for. Max 50
type `(optional)` | string | Filter type. Available values: `NAME`, `EMAIL`, `PHONE` or `ADDRESS`
create_from `(optional)` | string | Filter customer created from this date. Format `yyyy-mm-dd`
create_to `(optional)` | string | Filter customer created to this date. Format `yyyy-mm-dd`
category | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](#get-categories-2)
registration_status `(optional)` | string | Customer's registration status. Available values: `0` (unregistered), `1` (registered), `4` (blocked), `T` (inactive) or `R` (requested)
order_by `(optional)` | string | Order customers data. Available status: `LATEST_CUSTOMER` or `LAST_ORDER`
per_page `(optional)` | integer | Data per page. Default `10`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default `1`

## Get Customer Order Histories
> Example request:

```json

```
> Example response:

```json
{
  "total": {
    "items": 120,
    "orders": 47
  },
  "data": [
    {
      "order_id": 39384704,
      "po_number": 12000,
      "date": "2021-03-02 13:05:33",
      "total_price": 150000,
      "product_status": "S",
      "order_detail": [
        {
          "product_name": "Sepatu",
          "total": " 1"
        },
        {
          "product_name": "Kaos Merah ",
          "total": " 1"
        }
      ],
      "items": 2
    },
    {
      "order_id": 39384711,
      "po_number": 12007,
      "date": "2021-03-02 13:34:32",
      "total_price": 150000,
      "product_status": "S",
      "order_detail": [
        {
          "product_name": "Sepatu",
          "total": " 1"
        },
        {
          "product_name": "Kaos Merah ",
          "total": " 1"
        }
      ],
      "items": 2
    }
  ],
  "meta": {
    "pagination": {
      "total": 47,
      "count": 2,
      "per_page": 2,
      "current_page": 1,
      "total_pages": 24,
      "links": {
        "next": "https://api.ngorder.id/api/open/customer/order-history?id=123&per_page=2&pagination_offset=2"
      }
    }
  }
}
```
Get customer order histories

### Endpoint
` https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Customer's ID
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
per_page `(optional)` | integer | Data per page. Default `10`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default `1`

## Customer per Month
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": [
    {
      "total": 5,
      "date": "2020-09"
    },
    {
      "total": 9,
      "date": "2020-08"
    },
    {
      "total": 1653,
      "date": "2020-07"
    }
  ]
}
```
Get count of customers addes per month.

### Endpoint
`GET https://api.ngorder.id/api/open/customer/per-month`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token


## Download Customers Data
> Example request:

```json

```
> Example response:

```json
 {
     "response": "Success, your customer data will be sent to juragan@ngorder.id soon"
 }
```
Download customers data as Excel and send it to your email.

### Endpoint
`GET https://api.ngorder.id/api/open/customer/download`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
date `(optional)` | string | Filter the data by created date. Format `yyyy-mm`


## Update Customer Activation Status
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "message": "Budi has been blocked",
  "data": {
    "customer_id": "123",
    "name": "Budi"
  }
}
```
Change customer activation status

### Endpoint
`PATCH https://api.ngorder.id/api/open/customer/activation-status`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Customer's ID
status | string | Customer's status. Available values: `0` (refuse), `1` (accept), `2` (activate), `4` (block), `5` (delete), `6` (unblock)
category `(optional)` | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](#get-categories-2)


## Update Customer
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "customer_id": 123,
    "name": "Budi"
  }
}
```
Update customer's data.

### Endpoint
`PATCH https://api.ngorder.id/api/open/customer/update`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
customer_id | integer | Customer's ID taken from [Get Customers](#get-customers)
name `(optional)` | string | Customer's name
phone `(optional)` | numeric | Customer's phone number
district_id `(optional)` | numeric | District ID taken from [Region](#region)
address `(optional)` | string | Customer's detailed address
postal_code `(optional)` | numeric | Postal code
category `(optional)` | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](#get-categories-2)
line `(optional)` | string | Customer's Line ID
email `(optional)` | string | Customer's email
other `(optional)` | string | Customer's other contacts
is_active `(optional)` | string | Customer's activation status. Available values: `Y` (active), `N`  (non-active), `R` (requested customer) or `T` (unactivated Storefront customer email)