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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Product name or product variation SKU to look for
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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Product name to look for
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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
category `(optional)` | string | Product category. Available values: `UNCATEGORIZED`, `ARCHIVED` or the ID of [Product Category](/#product-category) that has been created
price `(optional)` | string | Product price status. Available values: `NON_SET_PRICE` or `NON_PROFIT`
channel `(optional)` | string | Product integration channel. Available values: `JURNAL` or `SHOPEE`
order_by `(optional)` | string | Order the data. Available values: `NEWEST`, `LONGEST`, `CHEAPEST`, `EXPENSIVE`, `LEAST_STOCK`, `MOST_STOCK`, `ASC` or `DESC`
keyword `(optional)` | string | Product name or product variation SKU to look for

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
token | string | Bearer token

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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | []integer | Product ID



# Customer Category
## Create Category
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 123,
    "category_name": "Pelanggan Tetap",
    "code": "2",
    "status": "NON ACTIVE",
    "discount_access": "1",
    "wholesale_access": "1"
  }
}
```
Create a customer category

### Endpoint
`POST https://api.ngorder.id/api/open/customer-category/create`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
category_name | string | Category name
discount_access `(optional)` | boolean | Discount access for this category.
wholesale_access `(optional)` | boolean | Wholesale access for this category.


## Get Categories
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "code": "N",
      "category_name": "Pelanggan",
      "status": "ACTIVE",
      "discount_access": true,
      "wholesale_access": true
    },
    {
      "id": 2,
      "code": "Y",
      "category_name": "Reseller",
      "status": "ACTIVE",
      "discount_access": true,
      "wholesale_access": false
    },
    {
      "id": 3,
      "code": "D",
      "category_name": "Dropship",
      "status": "ACTIVE",
      "discount_access": true,
      "wholesale_access": false
    },
    {
      "id": 122,
      "code": "1",
      "category_name": "Teman",
      "status": "ACTIVE",
      "discount_access": true,
      "wholesale_access": false
    },
    {
      "id": 123,
      "code": "2",
      "category_name": "Pelanggan Tetap",
      "status": "ACTIVE",
      "discount_access": true,
      "wholesale_access": true
    }
  ]
}
```
Get all customer category

### Endpoint
`GET https://api.ngorder.id/api/open/customer-category`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
status `(optional)` | string | Sort by categories active status. Available values: `N` or `Y`

## Update Customer Category
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 122,
    "code": "1",
    "category_name": "Teman",
    "status": "ACTIVE",
    "discount_access": true,
    "wholesale_access": false
  }
}
```
Update customer category

### Endpoint
`PATCH https://api.ngorder.id/api/open/customer-category/update`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Customer category ID
code | string | Customer category code
category_name `(optional)` | string | Category name
status `(optional)` | string | Active status. Available values: `Y` (active) or `N` (non active)
discount_access `(optional)` | string | Discount access for this category
wholesale_access `(optional)` | string | Wholesale access for this category

# Region
## Get Regions
> Example response:

```json
{
  "data": [
    {
      "_id": "5d1d86101449f91d8b32cdce",
      "id": 3627,
      "subdistrict": "Tajinan",
      "district": {
        "id": 255,
        "name": "Kabupaten Malang"
      },
      "province": {
        "id": 11,
        "name": "Jawa Timur"
      },
      "fullname": "Tajinan, Kabupaten Malang, Jawa Timur",
      "postal_code": [
        "65172"
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
Get region data that will be used when [creating a new customer](/#create-customer)

### Endpoint
`GET https://api.ngorder.id/api/open/region`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | District name to look for
per_page `(optional)` | integer | Data per page. Default `1`
pagination_offset | integer | Page number. Default `1`

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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
name | string | Customer's name
phone | numeric | Customer's phone number
district_id | numeric | District ID taken from [Region](/#region)
address | string | Customer's detailed address
postal_code `(optional)` | numeric | Postal code
category | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)
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
token | string | Bearer token

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
        "next": "http://api.ngorder.id/api/customer?pagination_offset=2"
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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Customer name to look for. Max 50
type `(optional)` | string | Filter type. Available values: `NAME`, `EMAIL`, `PHONE` or `ADDRESS`
create_from `(optional)` | string | Filter customer created from this date. Format `yyyy-mm-dd`
create_to `(optional)` | string | Filter customer created to this date. Format `yyyy-mm-dd`
category | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)
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
        "next": "http://api.ngorder.id/api/open/customer/order-history?id=123&per_page=2&pagination_offset=2"
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
token | string | Bearer token

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
token | string | Bearer token


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
token | string | Bearer token

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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Customer's ID
status | string | Customer's status. Available values: `0` (refuse), `1` (accept), `2` (activate), `4` (block), `5` (delete), `6` (unblock)
category `(optional)` | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)


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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
name `(optional)` | string | Customer's name
phone `(optional)` | numeric | Customer's phone number
district_id `(optional)` | numeric | District ID taken from [Region](/#region)
address `(optional)` | string | Customer's detailed address
postal_code `(optional)` | numeric | Postal code
category `(optionl)` | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)
line `(optional)` | string | Customer's Line ID
email `(optional)` | string | Customer's email
other `(optional)` | string | Customer's other contacts
is_active `(optional)` | string | Customer's activation status. Available values: `Y` (active), `N`  (non-active), `R` (requested customer) or `T` (unactivated Storefront customer email)


# Bank
## Get Master Data
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "bank_type": "bca",
      "bank_label": "Bank BCA",
      "bank_family": "bca",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bca.svg",
      "web_login_url": "https://www.klikbca.com",
      "status": 1
    },
    {
      "bank_type": "bcaSyariah",
      "bank_label": "Bank BCA Syariah",
      "bank_family": "bca",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bca.svg",
      "web_login_url": "https://ibank.klikbcasyariah.com",
      "status": 1
    },
    {
      "bank_type": "bni",
      "bank_label": "Bank BNI",
      "bank_family": "bni",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bni.svg",
      "web_login_url": "https://ibank.bni.co.id",
      "status": 1
    },
    {
      "bank_type": "bniBisnis",
      "bank_label": "Bank BNI Bisnis",
      "bank_family": "bni",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bni.svg",
      "web_login_url": "https://bnidirect.bni.co.id",
      "status": 1
    },
    {
      "bank_type": "bniBisnisSyariah",
      "bank_label": "Bank BNI Bisnis Syariah",
      "bank_family": "bni",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bni.svg",
      "web_login_url": "https://ibank.bni.co.id",
      "status": 1
    }
  ]
}
```
Get our main bank data.

### Endpoint
`GET https://api.ngorder.id/api/open/bank/master`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
without_business_bank `(optional)` | boolean | Exclude business bank. Default `false`

## Get Xendit Master Data
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "name": "Bank Sinarmas",
      "code": "SINARMAS",
      "can_disburse": 0,
      "can_name_validate": 0
    },
    {
      "id": 2,
      "name": "Bank Syariah Mandiri",
      "code": "MANDIRI_SYR",
      "can_disburse": 0,
      "can_name_validate": 0
    }
  ]
}
```
Get Xendit listed bank data

### Endpoint
` https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Bank name to look for


## Create Bank Account
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "bank_id": 26516,
    "name": "bca"
  }
}
```
Create bank account used in your shop.

### Endpoint
`POST https://api.ngorder.id/api/open/bank/create`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
bank_type | string | Bank type taken from [master data](/#get-master-data)
account_number | numeric | Bank account number
holder_name | string | Bank account holder name
branch | string | Bank branch
username `(optional)` | string | Bank username
pin `(optional)` | string | Bank pin
corporate_id | string | Corporate ID. Required if `bank_type` is a business bank

## Get Shop Bank Accounts
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "bank_id": 1,
      "bank_name": "BCA",
      "bank_type": "bca",
      "branch": "Mulyorejo",
      "holder_name": "Budi",
      "account_number": "12345678",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bca.svg",
      "type": "BANK"
    },
    {
      "bank_id": 2,
      "bank_name": "BNIS",
      "bank_type": "bni",
      "branch": "Srono",
      "holder_name": "Budi",
      "account_number": "12345678",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bnis.svg",
      "type": "BANK"
    }
  ]
}
```
Get bank data used in your shop.

### Endpoint
` https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type | string | Bank type. Available values: `BANK` or `PAYMENT GATEWAY`

## Get Bank Account Detail
> Example request:

```json

```
> Example response:

```json
{
  "bank_id": 1,
  "bank_name": "BCA",
  "bank_type": "bca",
  "branch": "Mulyorejo",
  "holder_name": "Budi",
  "account_number": "12345678",
  "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bca.svg",
  "type": "BANK"
}
```
Get detail of bank account used in your shop.

### Endpoint
`GET https://api.ngorder.id/api/open/bank/{id}/detail`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | numeric | Bank ID

## Update Bank Account
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "bank_id": 123,
    "name": "bca"
  }
}
```
Update bank account used in your shop.

### Endpoint
`PATCH https://api.ngorder.id/api/open/bank/update`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
bank_id | integer | Bank ID
bank_type | string | Bank type taken from [master data](/#get-master-data)
account_number `(optional)` | numeric | Bank account number
holder_name `(optional)` | string | Bank account holder name
branch `(optional)` | string | Bank branch
username `(optional)` | string | Bank username
pin `(optional)` | string | Bank pin
corporate_id | string | Corporate ID. Required if `bank_type` is a business bank

## Delete Mutation
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "bank_id": 100,
    "name": "mandiriBisnisMCM"
  }
}
```
Delete selected bank mutation.

### Endpoint
`DELETE https://api.ngorder.id/api/open/bank/delete-mutation/{bank_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
bank_id | integer | Bank ID

## Delete Bank
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": null
}
```
Delete bank account used in your shop.

### Endpoint
`DELETE https://api.ngorder.id/api/open/bank/delete/{bank_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
bank_id | integer | Bank ID

# Supplier
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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
name | string | Supplier name
district_id | numeric | District ID taken from [Region](/#region)
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
      "phone": "08212345678",
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
      "phone": "08212345678",
      "address": "JL. ABC",
      "description": "",
      "shipper_status": "ACTIVE"
    }
  ]
}
```
Get all suppliers

### Endpoint
`GET https://api.ngorder.id/api/open/supplier`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
supplier_id | integer | Supplier ID
name `(optional)` | string | Supplier name
district_id `(optional)` | numeric | District ID taken from [Region](/#region)
addess `(optional)` | string | Supplier detailed address
phone `(optional)` | numeric | Supplier phone number
description `(optional)` | string | Data description

# Warehouse
## Create Warehouse
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 23,
    "name": "Warehouse Jakarta"
  }
}
```
Create a warehouse.

### Endpoint
`POST https://api.ngorder.id/api/open/warehouse`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
warehouse | string | Warehouse name
supplier_id | integer | Supplier ID taken from [supplier](/#supplier)
user_id | []integer | User ID for this warehouse admin
is_active | boolean | Warehouse active status

## Get Warehouses
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "id": 22,
      "warehouse": "Warehouse Bandung",
      "supplier_id": 23518,
      "address": "Bandung Kulon, Kota Bandung"
    },
    {
      "id": 30,
      "warehouse": "Toko Utama",
      "supplier_id": 23519,
      "address": "Srono, Kabupaten Banyuwangi"
    }
  ]
}
```
Get all warehouse data.

### Endpoint
`GET https://api.ngorder.id/api/open/warehouse`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
with_main_warehouse `(optional)` | boolean | Includes main warehouse. Default `false`

## Get Warehouse Detail
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 22,
    "warehouse": "Warehouse Bandung",
    "supplier_id": 23518,
    "address": "Bandung Kulon, Kota Bandung"
  }
}
```
Get warehouse detailed data.

### Endpoint
`GET https://api.ngorder.id/api/open/warehouse/{id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Warehouse ID

## Update Warehouse
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 23,
    "name": "Warehouse Jakarta"
  }
}
```
Update a warehouse.

### Endpoint
`PATCH https://api.ngorder.id/api/open/warehouse`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Warehouse ID
warehouse | string | Warehouse name
supplier_id | integer | Supplier ID taken from [supplier](/#supplier)
user_id | []integer | User ID for this warehouse admin
is_active | boolean | Warehouse active status

## Delete Warehouse
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 22,
    "warehouse": "Warehouse Bandung",
    "supplier_id": 23518,
    "address": "Bandung Kulon, Kota Bandung"
  }
}
```
Delete selected warehouse.

### Endpoint
`DELETE https://api.ngorder.id/api/open/warehouse/{id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Warehouse ID

# Expedition
## Get Expeditions
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "rate_name": "REG",
      "logistic_name": "JNE",
      "show_name": "Regular",
      "pickup_available": "AVAILABLE"
    },
    {
      "id": 2,
      "rate_name": "YES",
      "logistic_name": "JNE",
      "show_name": "Express",
      "pickup_available": "AVAILABLE"
    },
    {
      "id": 3,
      "rate_name": "OKE",
      "logistic_name": "JNE",
      "show_name": "Regular",
      "pickup_available": "AVAILABLE"
    },
    {
      "id": 4,
      "rate_name": "CTC",
      "logistic_name": "JNE",
      "show_name": "Regular",
      "pickup_available": "AVAILABLE"
    }
  ]
}
```
Get all expeditions data

### Endpoint
`GET https://api.ngorder.id/api/open/expedition`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

## Get Active List
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "rate_name": "REG",
      "logistic_name": "JNE",
      "show_name": "Regular",
      "logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/jne.png",
      "pickup_available": "AVAILABLE"
    },
    {
      "id": 44,
      "rate_name": "REGPACK",
      "logistic_name": "Lion Parcel",
      "show_name": "Regular",
      "logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/lionparcel.png",
      "pickup_available": "AVAILABLE"
    }
  ],
  "meta": {
    "pagination": {
      "total": 4,
      "count": 4,
      "per_page": 2,
      "current_page": 1,
      "total_pages": 2,
      "links": {
        "next": "http://localhost:85/api/open/expedition/active?pagination_offset=2"
      }
    }
  }
}
```
Get expedition enabled for your shop. You can manage this by going <a href="https://app.ngorder.id/setting/courier" target="_blank">here</a> or on mobile app go to `Setting` > `Kurir` > `Kurir`.

### Endpoint
`GET https://api.ngorder.id/api/open/expedition/active`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Courier name to look for. Max `20`
per_page `(optional)` | integer | Data per page. Default `10`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default `1`


## Get Cost
> Example request:

```json

```
> Example response:

```json
{
  "status": {
    "code": 1,
    "message": "Success"
  },
  "data": {
    "regular": [
      {
        "name": "SAP",
        "logo_url": "http://cdn.shipper.cloud/logistic/small/SAP.png",
        "rate_id": 349,
        "show_id": 1,
        "rate_name": "Reguler",
        "stop_origin": 3870,
        "stop_destination": 5023,
        "weight": 1,
        "volumeWeight": 0.1667,
        "finalWeight": 1,
        "itemPrice": 120000,
        "item_price": 120000,
        "finalRate": 37500,
        "insuranceRate": 360,
        "compulsory_insurance": 0,
        "liability": 0,
        "discount": 0,
        "min_day": 3,
        "max_day": 3,
        "pickup_agent": 1,
        "is_pickup_available": 1
      }
    ],
    "express": [
      {
        "name": "SAP",
        "logo_url": "http://cdn.shipper.cloud/logistic/small/SAP.png",
        "rate_id": 350,
        "show_id": 2,
        "rate_name": "One Day Service",
        "stop_origin": 3870,
        "stop_destination": 5023,
        "weight": 1,
        "volumeWeight": 0.1667,
        "finalWeight": 1,
        "itemPrice": 120000,
        "item_price": 120000,
        "finalRate": 16000,
        "insuranceRate": 360,
        "compulsory_insurance": 0,
        "liability": 0,
        "discount": 0,
        "min_day": 1,
        "max_day": 1,
        "pickup_agent": 1,
        "is_pickup_available": 1
      }
    ],
    "trucking": []
  },
  "meta": {
    "origin": {
      "area_id": "334",
      "district_id": "334",
      "desc": "Padangbai, Manggis, Karangasem"
    },
    "destination": {
      "area_id": "11677",
      "district_id": "334",
      "desc": "Sukaresmi, Ranca Bali, Bandung, Kab."
    },
    "weight": {
      "total": "1",
      "type": "Kg"
    },
    "is_shipper_api": true,
    "use_cod": true
  }
}
```
Get expedition cost.

### Endpoint
`GET https://api.ngorder.id/api/open/expedition/cost`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
origin_id | integer | District ID taken from [Region](/#region)
destination_id | numeric | District ID taken from [Region](/#region)
weight | integer | Total product weight
price | integer | Total price without shipping cost
is_privor `(optional)` | boolean | Privor status. Default `false`
is_shipper `(optional)` | boolean | Shipper status. Default `false`

## Tracking
> Example request:

```json

```
> Example response:

```json
{
  "0": 200,
  "response": "success",
  "data": {
    "awb_number": "00046512912705",
    "rate_name": "REG",
    "delivery_date": "2021-01-02 18:55",
    "delivery_time": "2021-01-02 18:55",
    "weight": 1,
    "sender_name": "Keren Shop Id",
    "origin_city": "Bandung",
    "receiver_name": "Tusfendi",
    "receiver_address": "Gedebage, Bandung",
    "receiver_city": "Gedebage, Bandung",
    "status": "DELIVERED",
    "consignees_name": null,
    "date_received": null,
    "time_received": null,
    "history": [
      {
        "date": "2021-01-02 10:58:00",
        "desc": "PICKREQ",
        "location": "Terima permintaan pick up dari [Tokopedia]"
      },
      {
        "date": "2021-01-02 18:55:00",
        "desc": "IN",
        "location": "Paket telah di input (manifested) di Bandung [Bandung Sumberasih]"
      },
      {
        "date": "2021-01-02 21:29:00",
        "desc": "OUT",
        "location": "Paket keluar dari Bandung [Bandung Sumberasih]"
      },
      {
        "date": "2021-01-03 08:25:00",
        "desc": "IN",
        "location": "Paket telah di terima di Bandung [Bandung Rancasari]"
      },
      {
        "date": "2021-01-03 10:07:00",
        "desc": "ANT",
        "location": "Paket dibawa [SIGESIT - Suhendra]"
      },
      {
        "date": "2021-01-03 12:48:00",
        "desc": "DELIVERED",
        "location": "Paket diterima oleh [Kamil - (YBS) Yang Bersangkutan]"
      }
    ],
    "logistic_name": "sicepat"
  }
}
```
Track air waybill number

### Endpoint
`GET https://api.ngorder.id/api/open/expedition/tracking`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
awb_number | string | Air waybill number
expedition_id | integer | Expedition ID taken from [Get Expeditions](/#get-expeditions)
order_id | integer | Order ID
# Marketplace
## Get Marketplaces
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "marketplace_id": 1,
      "marketplace_name": "Tokopedia"
    },
    {
      "marketplace_id": 2,
      "marketplace_name": "Bukalapak"
    },
    {
      "marketplace_id": 3,
      "marketplace_name": "Shopee"
    },
    {
      "marketplace_id": 4,
      "marketplace_name": "Instagram"
    },
    {
      "marketplace_id": 5,
      "marketplace_name": "Whatsapp"
    },
    {
      "marketplace_id": 6,
      "marketplace_name": "Lazada"
    },
    {
      "marketplace_id": 7,
      "marketplace_name": "Facebook"
    },
    {
      "marketplace_id": 8,
      "marketplace_name": "Website Lain"
    }
  ]
}
```
Get marketplaces.

### Endpoint
`GET https://api.ngorder.id/api/open/marketplace`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
marketplace_id | integer | Marketplace ID taken from [Marketplaces](/#get-marketplaces)
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
token | string | Bearer token

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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
order_source_id | integer | Order source ID
marketplace_id `(optional)` | integer | Marketplace ID taken from [Marketplaces](/#get-marketplaces)
note `(optional)` | string | Order source name
status `(optional)` | string | Active status. Available values: `Y` or `N`




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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
category | string | Order cost category. Available values: `DISCOUNT` or `OTHER COST`
name | string | Order cost name
type | string | Order cost type. Available values: `NOMINAL` or `PERCENTAGE`
nominal | integer | Order cost nominal. Required if `type: NOMINAL`
percentage | integer | Order cost percentage. Required if `type: PERCENTAGE`


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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
order_cost_id | integer | Order cost ID



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
token | string | Bearer token

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
token | string | Bearer token

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
> Example response:

```json
{
  "request_id": "5f967ba06a030",
  "response": "Success",
  "message": "Order created",
  "data": {
    "order_id": 1237,
    "po_number": 10638
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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
customer_sender_id | integer |  Customer sender ID taken from [Customer](/#customer)
customer_receiver_id | integer | Customer receiver ID taken from [Customer](/#customer)
supplier_id | integer | Supplier ID taken from [Supplier](/#supplier)
order_date | string | Order date. Format `yyyy-mm-dd`
order_source_id `(optional)` | integer | Order source ID taken from [Order Source](/#order-source)
note `(optional)` | string | Note for the order
is_print | boolean | Order print status
products | []integer | Product variants ID
expedition | array | Expedition detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>id</td><td>`integer` Expedition ID</td></tr><tr><td>rate</td><td>`integer` Expedition cost</td></tr><tr><td>name</td><td>`string` Expedition name</td></tr><tr><td>auto_pickup</td><td>`boolean` Expedition auto pickup status</td></tr><tr><td>discount_promo `(optional)`</td><td>`integer` Expedition discount nominal</td></tr><tr><td>promo `(optional)`</td><td>`array` Promo detail from [Product Variants](/#get-product-variations)</td></tr></table>
payment | array | Payment detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>status</td><td>`string` Payment status. Available values: `PAID`, `INSTALLMENT` or `UNPAID`</td></tr><tr><td> date</td><td>`string` Payment date. Required if `status: PAID or INSTALLMENT`. Format `yyy-mm-dd`</td></tr><tr><td>bank_id</td><td>`integer` Bank ID. Required if `status: PAID or INSTALLMENT` taken from [Bank Accounts](/#get-shop-bank-accounts)</td></tr><tr><td>amount</td><td>`integer` Payment amount. Required if `status: PAID or INSTALLMENT`</td></tr><tr><td>cost_of_goods_sales</td><td>`integer` Cost to be paid to the supplier. Required if `product_status: R` (see [Create a Product](/#create-product))</td></tr></table>
order_cost `(optional)` | array | Other cost detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>name</td><td>`string` Order cost name</td></tr><tr><td>category</td><td>`string` Cost category. Available values: `DISCOUNT`, `OTHER COST` or `INSURANCE`</td></tr><tr><td>type</td><td>`string` Cost type. Available values: `NOMINAL` or `PERCENTAGE`</td></tr><tr><td>percentage</td><td>`integer` Order cost percentage. Required if `type: PERCENTAGE`</td></tr><tr><td>nominal</td><td>`integer` Order cost nominal. Required if `type: NOMINAL`</td></tr></table>
awb_number `(optional)` | string | Air waybill number
send_sms `(optional)` | boolean | SMS status. Default value: `false`
marketplace_awb `(optional)` | string | Marketplace air waybill
source | string | Source platform. Available values: `MOBILE` or `WEB`

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
        "next": "http://api.ngorder.id/api/open/order?pagination_offset=2"
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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Keyword to look for
payment_status `(optional)` | string | Filter by payment status. Available values: `UNPAID`, `PAID` or `INSTALLMENT`
order_progress_status | string | Filter by order progress status. Available values: `UNPAID`, `NO AWB`, `ON PROCESS`, `DELIVERED`, `UNPROCESSED` or `INSTALLMENT`
order_category `(optional)` | string | Order category. Available values: `APP`, `PRIVOR`, `STORE_FRONT`, `SHOPEE`, `QUICK_ORDER` or `UNCATEGORIZED`
order_source_id `(optional)` | integer | Sales channel ID taken from [Order Source](/#get-order-sources)
shipping_id `(optional)` | integer | Expedition ID taken from [Get Expeditions](/#get-expeditions)
type `(optional)` | string | Order type. Available values: `ORDER_ID`, `CUSTOMER_NAME`, `AWB_NUMBER`, `CUSTOMER_PHONE`, `SHOPEE_INVOICE`, `PRODUCT_NAME`, `SKU` or `SHIPPER_TRACKING`
order_by `(optional)` | string | Order the data. Available values: `ORDER_DATE` or `PAYMENT_DATE`. Default value: `ORDER_DATE`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`. Default value: 30 days ago
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`. Default value: today
user_id `(optional)` | integer | The ID of admin who made this order
bank_id `(optional)` | integer | Bank ID taken from [Bank Accounts](/#get-shop-bank-accounts)
warehouse_id  `(optional)` |  integer | Product variant warehouse ID taken from [Stock per Warehouse](#check-stock-per-warehouse)
customer_category_code `(optional)` | integer | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)
expedition_id  | |
pickup `(optional)` | integer | Pickup status. Available values: `0` (ready to send), `1` (pickup request) or `2` (delivered)
print_status `(optional)` | string | Print status. Available value: `Y` or `N`
product_type `(optional)` | string | Product stock type. `S` (own stock), `R` (from other suppliers), `PO` (preorder)
per_page `(optional)` | integer | Data per page. Default `10`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default `1`




## Get Orders Detail


## Get Single Order Detail




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


> Example request:

```json
```
> Example response:

```json

```
Create an order cost

### Endpoint
` https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
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
