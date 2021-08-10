---
title: Ngorder API - Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - JSON

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Ngorder provides API that can be used to integrate your system with our platform. The API is built based on REST concept and will return JSON formatted data upon your requests. In order to use our API, you must have an existing active shop in our application.

## Types of Parameter Location
> Example of body parameter:

```json
{
  "param_1": 1,
  "param_2": 2
}
```

### Body

A JSON that sent with the request, usually used in POST or PATCH requests.

### Path
Located inside the URL used to identify a resource uniquely, usually used in GET requests. example:

`https://api.ngorder.id/api/open/resource/{id}`

### Query
Located inside the URL that appear after question mark, it's usually optional and used in GET requests. example:

`https://api.ngorder.id/api/open/resource?{key=value}`

<!-- Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation. -->

# Authentication

In order to use our API, you can securely authorize your application using either Key Authentication or OAuth 2, this key will be available if you are using our [**Platinum package**](https://app.ngorder.id/upgrade?app=platinum-12), if you're already using our Platinum package be sure to check your key as it's updated every year. Both authorization method provide access to the same API, only the endpoints are slightly different.

<!-- > To authorize, use this code: -->

<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
``` -->

<!-- > Make sure to replace `meowmeowmeow` with your API key. -->


<!-- <aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside> -->

# User
## Get Users
> Example response:

```json
{
  "response": "Success",
  "data": [
    {
      "id": 1,
      "name": "User One",
      "email": "user1@example.com"
    },
    {
      "id": 2,
      "name": "User Two",
      "email": "user2@example.com"
    },
  ]
}
```

Get user all users data within your shop

### Endpoint
`GET https://api.ngorder.id/api/open/user

### Header
Parameter | type | Description
--------- | ---- | -----------
token | string | Bearer Token

## Update Profile
> Example response:

```json
{
  "response": "success",
  "data": {
    "full_name": "User 1",
    "phone_number": "0812345678"
  }
}
```

### Endpoint
`PATCH https://api.ngorder.id/api/open/user/profile`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Body
Parameter | Type | Description
--------- | ---- | -----------
full_name | string | User full name
phone_number | numeric | User phone number
password `(optional)` | string | User password
password_confirmation `(optional)` | string | User password confirmation. Required if `password` is filled.


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
token | string | Bearer Token

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
token | string | Bearer Token

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
token | string | Bearer Token

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
token | string | Bearer Token

### Body
Parameter | Type | Description
--------- | ---- | -----------
shop_name | string | Shop name
phone | string | Shop phone number
description | string | Shop description
address | string | Shop address
logo | string | Shop logo url

# Product Category
## Create Category
> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 1,
    "name": "FASHION"
  }
}
```
Create product category.

### Endpoint
`POST https://api.ngorder.id/api/open/product-category`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Body
Parameter | Type | Description
--------- | ---- | -----------
name | string | Product category name

## Get Categories
> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "name": "FASHION"
    },
    {
      "id": 2,
      "name": "BOOKS"
    }
  ]
}
```
Get product categories.

### Endpoint
`GET https://api.ngorder.id/api/open/product-category`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

## Get Category Detail
> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 1,
    "name": "Fashion"
  }
}
```
Get single product category.

### Endpoint
`GET https://api.ngorder.id/api/open/product-category/{id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Product category ID 

## Update Category
> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 23,
    "name": "GAMIS ZIZARA"
  }
}
```
Update product category.

### Endpoint
`PATCH https://api.ngorder.id/api/open/product-category`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Product category ID
name | string | Product category name

## Delete Category
> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 23,
    "name": "GAMIS ZIZARA"
  }
}
```
Delete a product category.

### Endpoint
`DELETE https://api.ngorder.id/api/open/product-category/{id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Product category ID

# Product
## Generate Product SKU
> Example request:

```json
{
  "products": [
    {
      "name": "Sepatu",
    }
  ]
}
```
> Example response:

```json
{
  "response": "Success",
  "data": [
    {
      "name": "Sepatu",
      "color": "",
      "size": "",
      "sku": "SEP-Pq2",
      "old_sku": ""
    }
  ]
}
```
Generate SKU for product.

### Endpoint
`GET https://api.ngorder.id/api/open/product/sku/generate-new`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Body
Parameter | Type | Description
--------- | ---- | -----------
products | array | Product details
products[name] | string | Product name
products[color] `(optional)` | string | Product color
products[size] `(optional)` | string | Product size
products[old_sku] `(optional)` | string | Product old SKU

## Validate SKU
> Example request:

```json
{
  "sku": "SEP-PUT-KhX",
  "product_meta_id": 2
}
```
> Example response:

```json
 {
    "response": "Success",
    "data": {
        "status": true,
        "variation": "putih",
        "product_id": ""
    }
 }
```
Validate product SKU.

### Endpoint
`POST https://api.ngorder.id/api/open/product/sku/validation`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Body
Parameter | Type | Description
--------- | ---- | -----------
sku | string | Product SKU
product_meta_id | integer | Product variant ID

## Create Product
> Example request:

```json
{
  "name": "Sepatu",
  "product_type": "S",
  "category_id": 0,
  "description": "Sepatu Bagus",
  "discount": 0,
  "weight": 100,
  "wholesale_status": "N",
  "shop_id": 1,
  "user_id": 1,
  "is_warehouse": "0",
  "publish_status": "N",
  "show_stock": "N",
  "has_variation": "Y",
  "variations": [
    {
      "sku": "SEP-MER-KhC",
      "primary_image": null,
      "image": null,
      "images": null,
      "weight": 100,
      "price_buy": 1000,
      "price": 5000,
      "price_reseller": 2000,
      "price1": 2000,
      "price2": 2000,
      "price3": 2000,
      "size": null,
      "color": "merah",
      "is_warehouse": false,
      "stock_quantity": 5,
      "stock": "Y",
      "warehouse_stock": []
    },
    {
      "sku": "SEP-PUT-KhX",
      "primary_image": null,
      "image": null,
      "images": null,
      "weight": 100,
      "price_buy": 1000,
      "price": 5000,
      "price_reseller": 2000,
      "price1": 2000,
      "price2": 2000,
      "price3": 2000,
      "size": null,
      "color": "putih",
      "is_warehouse": false,
      "stock_quantity": 3,
      "stock": "Y",
      "warehouse_stock": []
    }
  ],
  "wholesales": []
}
```

> Example response:

```json
{
  "response": "Success",
  "message": "Data successfully saved",
  "data": {
    "product_id": 1,
    "product_meta_id": [
      1,
      2
    ],
    "total_stock": 8
  }
}
```
Create a product.

### Endpoint
`POST https://api.ngorder.id/api/open/product`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Body
Parameter | Type | Description
--------- | ---- | -----------
name | string | Product name
product_type | string | Product stock type. `S` (own stock), `R` (from other suppliers), `PO` (preorder)
category_id | integer | Product category ID
description | string | Product description
preorder_setting `(optional)` | array | Preorder setting. Required if `product_type: PO`
preorder_setting[type] `(optional)` | string | Preorder type. Available values: `day` or `week`
preorder_setting[number] `(optional)` | numeric | Number of weeks or days. Max 90 days or 12 weeks
shop_id | integer | Shop ID
user_id | integer | User ID
discount | integer | Product discount amount
wholesale_status | string | Product wholesale status. Available values: `Y` or `N`
wholesale `(optional)` | array | Wholesale data
wholesale[from] `(optional)` | numeric | Minimum products bought before wholesale is applied
wholesale[to] `(optional)` | numeric | Maximum products bought before wholesale is applied
wholesale[price] `(optional)` | Product wholesale price
is_warehouse `(optional)` | integer | Product warehouse status. Available value: `1` or `0`. Default: `0`
publish_status | string | Product publish status. Available values: `Y` or `N`
show_stock | string | Show product stock in Storefront or Privor status. Available value: `Y` or `N`
has_variation | string | Product variation status. Available value: `Y` or `N`
variations | array | Product variations details
variations[sku] | string | Product variation SKU
variations[images] | array | Product variation images URL. Array of string with maximum of 5 URLs
variations[primary_image] | numeric | Product variation primary image. Index of `variations[images]` start from `0` to `4`
variations[price_buy] | integer | Product variation purchase price
variations[price] | integer | Product variation price
variations[price1] | integer | Product variation price for the first custom customer category  
variations[price2] | integer | Product variation price for the second custom customer category 
variations[price3] | integer | Product variation price for the third custom customer category   
variations[price_reseller] | integer | Product price for reseller
variations[size] | string | Product variation size
variations[color] | string | Product variation color
variations[stock] | string | Product variation stock status. Required if `product_type: R or PO`. Available values: `Y` (in stock) or `N` (out of stock)
variations[stock_quantity] `(optional)` | integer | Product variation stock quantity. Required if `product_type: S`. Min 0
variations[warehouse_stock] | array | Warehouse stock data
...warehouse_stock[warehouse_id] | integer |  Warehouse ID
...warehouse_stock[stock] | integer | Warehouse stock quantity

## Get Products
> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "name": "Sepatu",
      "product_type": "S",
      "type_description": "Stok Sendiri",
      "category_id": 1,
      "category_name": "",
      "description": "Sepatu Bagus",
      "discount": 0,
      "weight": 100,
      "is_warehouse": false,
      "publish_status": "N",
      "shop_id": 1,
      "user_id": 1,
      "show_stock": "N",
      "total_stock": 8,
      "wholesale_status": "N",
      "has_variation": "Y",
      "image": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
      "thumbnail": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
      "wholesales": [],
      "variations": [
        {
          "id": 1,
          "sku": "SEP-MER-KhC",
          "image": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
          "thumbnail": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
          "weight": 100,
          "size": "",
          "color": "merah",
          "price_buy": 1000,
          "price": 5000,
          "price_reseller": 2000,
          "price1": 2000,
          "price2": 2000,
          "price3": 2000,
          "stock_quantity": 5,
          "stock": "Y"
        },
        {
          "id": 2,
          "sku": "SEP-PUT-KhX",
          "image": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
          "thumbnail": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
          "weight": 100,
          "size": "",
          "color": "putih",
          "price_buy": 1000,
          "price": 5000,
          "price_reseller": 2000,
          "price1": 2000,
          "price2": 2000,
          "price3": 2000,
          "stock_quantity": 2,
          "stock": "Y"
        }
      ],
      "update_access": true,
      "warehouse": [
        {
          "name": "Gudang Utama",
          "id": 0
        }
      ]
    }
  ],
  "meta": {
    "pagination": {
      "total": 1,
      "count": 1,
      "per_page": 10,
      "current_page": 1,
      "total_pages": 1,
      "links": {}
    }
  }
}
```
Get product list.

### Endpoint
`GET https://api.ngorder.id/api/open/product/search`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Product name or product variation SKU
shop_id `(optional)` | integer | Shop ID
category `(optional)` | string | Product category. Available values: `UNCATEGORIZED`, `ARCHIVED` or the ID of [Product Category](/#product-category) that has been created
type `(optional)` | string | Product stock type. Available values: `S` (own stock), `R` (from other suppliers), `PO` (preorder)
price `(optional)` | string | Product price status. Available values: `NON_SET_PRICE` or `NON_PROFIT`
channel `(optional)` | string | Product integration channel. Available values: `JURNAL` or `SHOPEE`
order_by `(optional)` | string | Order the data. Available values: `NEWEST`, `LONGEST`, `CHEAPEST`, `EXPENSIVE`, `LEAST_STOCK`, `MOST_STOCK`, `ASC` or `DESC`
pagination_offset `(optional)` | integer | Page number

## Get Product Detail
> Example response:

```json
{
  "response": "Sukses",
  "data": {
    "id": 1,
    "name": "Sepatu",
    "product_type": "S",
    "type_description": "Stok Sendiri",
    "preorder_setting": null,
    "category_id": 1,
    "category_name": "",
    "description": "Sepatu Bagus",
    "discount": 0,
    "weight": 100,
    "is_warehouse": false,
    "publish_status": "N",
    "shop_id": 1,
    "user_id": 1,
    "show_stock": "N",
    "total_stock": 7,
    "wholesale_status": "N",
    "has_variation": "Y",
    "image": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
    "thumbnail": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
    "variations": [
      {
        "id": 1,
        "sku": "SEP-MER-KhC",
        "primary_image": null,
        "image": null,
        "images": null,
        "thumbnail": null,
        "thumbnails": [],
        "weight": 100,
        "size": "",
        "color": "merah",
        "price_buy": 1000,
        "price": 5000,
        "price_reseller": 2000,
        "stock_quantity": 5,
        "stock": "Y",
        "price1": 2000,
        "price2": 2000,
        "price3": 2000
      },
      {
        "id": 2,
        "sku": "SEP-PUT-KhX",
        "primary_image": null,
        "image": null,
        "images": null,
        "thumbnail": null,
        "thumbnails": [],
        "weight": 100,
        "size": "",
        "color": "putih",
        "price_buy": 1000,
        "price": 5000,
        "price_reseller": 2000,
        "stock_quantity": 2,
        "stock": "Y",
        "price1": 2000,
        "price2": 2000,
        "price3": 2000
      }
    ],
    "wholesale_prices": []
  }
}
```
Get product detail

### Endpoint
`GET https://api.ngorder.id/api/open/product/{product_id}/detail`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Path
Parameter | Type | Description
--------- | ---- | -----------
product_id | integer | Product ID



## Check Product Stock
> Example response:

```json
{
  "response": "Success",
  "data": {
    "stock": 10,
    "price": 10000,
    "price_dropship": 12100,
    "price1": 12000,
    "price2": 12500,
    "price3": 12700
  }
}
```
Check product stock.

### Endpoint
`GET https://api.ngorder.id/api/open/product/check-stock`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Query
Parameter | Type | Description
--------- | ---- | -----------
variation_id | integer | Product variant ID
warehouse_id `(optional)` | integer | Warehouse I

## Check Stock per Warehouse
> Example response:

```json
{
  "data": [
    {
      "warehouse_id": 1,
      "name": "Gudang Malang",
      "stock": 172
    },
    {
      "warehouse_id": 2,
      "name": "Gudang Surabaya",
      "stock": 189
    }
  ]
}
```
Get stock data of product variant in warehouses.

### Endpoint
`GET https://api.ngorder.id/api/open/product/history/warehouse/{variation_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Path
Parameter | Type | Description
--------- | ---- | -----------
variation_id | integer | Product variant ID

## Get Product Variations
> Example response:

```json
{
  "data": [
    {
      "variation_id": 2,
      "product_id": 1,
      "name": "Sepatu",
      "product_type": "S",
      "type_description": "Stok Sendiri",
      "preorder_title": null,
      "publish_status": "N",
      "stock_quantity": 5,
      "sku": "SEP-MER-KhC",
      "image": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
      "thumbnail": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
      "discount": 0,
      "color": "",
      "size": "merah",
      "weight": 100,
      "category_id": 0,
      "created_at": "2021-08-09T10:44:08+07:00",
      "price": 5000,
      "price1": 2000,
      "price2": 2000,
      "price3": 2000,
      "price_reseller": 2000,
      "price_buy": 1000,
      "wholesale_status": "N",
      "is_warehouse": 0,
      "warehouse_stock": null,
      "promo": []
    },
    {
      "variation_id": 2,
      "product_id": 1,
      "name": "Sepatu",
      "product_type": "S",
      "type_description": "Stok Sendiri",
      "preorder_title": null,
      "publish_status": "N",
      "stock_quantity": 0,
      "sku": "SEP-PUT-KhX",
      "image": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
      "thumbnail": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
      "discount": 0,
      "color": "",
      "size": "putih",
      "weight": 100,
      "category_id": 0,
      "created_at": "2021-08-09T10:44:08+07:00",
      "price": 5000,
      "price1": 2000,
      "price2": 2000,
      "price3": 2000,
      "price_reseller": 2000,
      "price_buy": 1000,
      "wholesale_status": "N",
      "is_warehouse": 0,
      "warehouse_stock": null,
      "promo": []
    }
  ]
}
```
Get product variations.

### Endpoint
`GET https://api.ngorder.id/api/open/product/variation`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Product name
per_page `(optional)` | integer | Variation data per page
customer_id `(optional)` | integer | Customer ID. For checking product promo availability

## Get Product Variation Histories
> Example response:

```json
{
  "title": {
    "product_id": 1,
    "variation_id": 1,
    "product_name": "Sepatu",
    "variation_name": " merah"
  },
  "data": [
    {
      "date": "Senin, 9 Ags 2021",
      "time_ago": "5 jam yang lalu",
      "user": "juragan@ngorder.id",
      "detail": {
        "description": "Initial variation stock on 2021-08-09",
        "id_order": null
      },
      "warehouse": {
        "id": null,
        "name": null
      },
      "stock": {
        "in": 5,
        "out": 0,
        "last": 5
      },
      "old": 0
    }
  ],
  "meta": {
    "pagination": {
      "total": 1,
      "count": 1,
      "per_page": 10,
      "current_page": 1,
      "total_pages": 1,
      "links": []
    }
  }
}
```
Get product variant histories.

### Endpoint
`GET https://api.ngorder.id/api/open/product/history`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Query
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Product variant ID
warehouse_id `(optional)` | integer | Variant warehouse ID. Taken from [Stock per Warehouse](/#check-stock-per-warehouse) response
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
per_page `(optional)` | integer | Data per page. Default `10`
pagination_offset `(optional)` | integer | Page number. Default `1`

## Get Wholesale Minimum
> Example response:

```json
 {
    "response": "success",
    "data": {
        "product_id": 123,
        "minimum_quantity": 30
    }
 }
```
Get wholesale minimum products bought before gets applied

### Endpoint
`GET https://api.ngorder.id/api/open/product/wholesale`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Query
Parameter | Type | Description
--------- | ---- | -----------
product_id | integer | Product ID

## Update Product
> Example request:

```json
{
  "id": 1,
  "name": "Sepatu",
  "product_type": "S",
  "category_id": 0,
  "description": "Sepatu Bagus Sekali",
  "discount": 0,
  "weight": 100,
  "wholesale_status": "N",
  "shop_id": 1,
  "user_id": 1,
  "is_warehouse": "0",
  "publish_status": "N",
  "show_stock": "N",
  "has_variation": "Y",
  "variations": [
    {
      "id": 1,
      "sku": "SEP-MER-KHC",
      "primary_image": null,
      "image": null,
      "images": [],
      "weight": 100,
      "price_buy": 1000,
      "price": 5000,
      "price_reseller": 2000,
      "price1": 2000,
      "price2": 2000,
      "price3": 2000,
      "size": "",
      "color": "merah",
      "is_warehouse": false,
      "stock_quantity": 10,
      "stock": "Y",
      "warehouse_stock": []
    },
    {
      "id": 2,
      "sku": "SEP-PUT-KHX",
      "primary_image": null,
      "image": null,
      "images": [],
      "weight": 100,
      "price_buy": 1000,
      "price": 5000,
      "price_reseller": 2000,
      "price1": 2000,
      "price2": 2000,
      "price3": 2000,
      "size": "",
      "color": "putih",
      "is_warehouse": false,
      "stock_quantity": 0,
      "stock": "Y",
      "warehouse_stock": []
    }
  ],
  "wholesales": []
}
```

> Example response:

```json
{
  "response": "Success",
  "message": "Data successfully saved",
  "data": {
    "product_id": 1,
    "product_meta_id": [
      1,
      2
    ],
    "total_stock": 10
  }
}
```

Update a product.

### Endpoint
`PATCH https://api.ngorder.id/api/open/product`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Product ID
name | string | Product name
product_type | string | Product stock type. `S` (own stock), `R` (from other suppliers), `PO` (preorder)
category_id | integer | Product category ID
description | string | Product description
preorder_setting `(optional)` | array | Preorder setting. Required if `product_type: PO`
preorder_setting[type] `(optional)` | string | Preorder type. Available values: `day` or `week`
preorder_setting[number] `(optional)` | numeric | Number of weeks or days. Max 90 days or 12 weeks
shop_id | integer | Shop ID
user_id | integer | User ID
discount | integer | Product discount amount
wholesale_status | string | Product wholesale status. Available values: `Y` or `N`
wholesale `(optional)` | [][Wholesale](/#update-product-wholesale-data) | Wholesale data
is_warehouse `(optional)` | integer | Product warehouse status. Available value: `1` or `0`. Default: `0`
publish_status | string | Product publish status. Available values: `Y` or `N`
show_stock | string | Show product stock in Storefront or Privor status. Available value: `Y` or `N`
has_variation | string | Product variation status. Available value: `Y` or `N`
variations `(optional)` | [][Variations](/#update-product-variations-data) | Product variations details

<span id="update-product-wholesale-data"></span>

__Wholesale Data__

Key | Type | Description
--------- | ---- | -----------
id | integer | Product wholesale ID
from | numeric | Minimum products bought before wholesale is applied
to | numeric | Maximum products bought before wholesale is applied
price | Product wholesale price

<span id="update-product-variations-data"></span>

__Variations Data__

Key | Type | Description
--------- | ---- | -----------
id | string | Product variant ID
flag | string | To delete selected variant fill `DELETE`
sku | string | Product variation SKU
images | array | Product variation images URL. Array of string with maximum of 5 URLs
primary_image | numeric | Product variation primary image. Index of `variations[images]` start from `0` to `4`
price_buy | integer | Product variation purchase price
price | integer | Product variation price
price1 | integer | Product variation price for the first custom customer category  
price2 | integer | Product variation price for the second custom customer category 
price3 | integer | Product variation price for the third custom customer category   
price_reseller | integer | Product price for reseller
size | string | Product variation size
color | string | Product variation color
stock | string | Product variation stock status. Required if `product_type: R or PO`. Available values: `Y` (in stock) or `N` (out of stock)
stock_quantity | integer | Product variation stock quantity. Required if `product_type: S`. Min 0

## Update Stock
> Example request:

```json
{
    "variation_id": 123,
    "stock": [
        {
            "amount": 10,
            "status": "add",
            "warehouse_id": 1
        },
        {
            "amount": 10,
            "status": "add",
            "warehouse_id": 3
        }
    ],
    "description": "Tambahan stok bulan ini",
    "move_warehouse_stock": true
}
```

> Example response:

```json
{
  "response": "Success",
  "data": {
    "date": "2020-10-14T07:39:32.661567Z",
    "variation_id": 123,
    "stock": [
      {
        "amount": 10,
        "status": "sub",
        "warehouse_id": 1
      },
      {
        "amount": 10,
        "status": "add",
        "warehouse_id": 3
      }
    ],
    "shop_id": 1,
    "description": "Tambahan stok bulan ini",
    "total_stock": 200
  }
}
```
Update product stock

### Endpoint
`PATCH https://api.ngorder.id/api/open/product/update-stock`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Body
Parameter | Type | Description
--------- | ---- | -----------
variation_id | integer | Product variant ID
stock | array | Stock data
stock[amount] | integer | New product variant stock
stock[status] | string | Update status. Available values: `ADD` or `SUB`
stock[warehouse_id] | integer | Warehouse ID
move_warehouse_stock `(optional)` | boolean | Move updated stock to warehouse. Available values: `true` or `false`. Default `false`
description | string | Update stock description


## Sync Stock
> Example request:

```json
{
  "variation_id": 1,
  "amount": 20
}
```

> Example response:

```json
{
  "response": "Success",
  "data": {
    "variation_id": "1",
    "amount": "30",
    "request_id": "607f5cc501931"
  }
}
```
Sync product variant stock.

### Endpoint
`PATCH https://api.ngorder.id/api/open/product/sync-stock`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Body
Parameter | Type | Description
--------- | ---- | -----------
variation_id | integer | Product variant ID
amount | integer | New stock amount

## Download
> Example response:

```json
 {
     "response": "Success, your product data will be sent to juragan@ngorder.id soon"
 }
```
Download products data as Excel and send it to your email.

### Endpoint
`GET https://api.ngorder.id/api/open/product/download`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Query
Parameter | Type | Description
--------- | ---- | -----------
category `(optional)` | string | Product category. Available values: `UNCATEGORIZED`, `ARCHIVED` or the ID of [Product Category](/#product-category) that has been created
price `(optional)` | string | Product price status. Available values: `NON_SET_PRICE` or `NON_PROFIT`
channel `(optional)` | string | Product integration channel. Available values: `JURNAL` or `SHOPEE`
order_by `(optional)` | string | Order the data. Available values: `NEWEST`, `LONGEST`, `CHEAPEST`, `EXPENSIVE`, `LEAST_STOCK`, `MOST_STOCK`, `ASC` or `DESC`
keyword `(optional)` | string | Product name or product variation SKU

## Delete Variation
> Example request:

```json
{
  "id": [
    123,
    124
  ]
}
```

> Example response:

```json
{
  "response": "success",
  "message": "Data has been deleted"
}
```
Delete product variations.

### Endpoint
`DELETE https://api.ngorder.id/api/open/product/variation`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | []integer | Product variants ID

## Delete Products
> Example request:

```json
{
  "id": [
    1,
    2,
    3
  ]
}
```

> Example response:

```json
{
  "response": "success",
  "message": "Data has been deleted"
}
```
Delete products.

### Endpoint
`DELETE https://api.ngorder.id/api/open/product`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer Token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | []integer | Product ID



# Customer
## Customer Category
## Customer Create
## Customer Read
## Customer Update
## Customer Delete

# Bank Account

# Warehouse -opt

# Supplier

# Expedition

# Order
## Order Source -opt
## Order Cost -opt
## Order CRUD

# Storefront & Privor
## Order Confirmation
## Setting Storefront Courier

# Shipment
# Payment
## Virtual Account Transaction
## Setting Payment Fee

# Expense

# Report

# Analyzer

# Notification

# Billing

# Woowa
## Customer
## Order

<!-- ## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->
