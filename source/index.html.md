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
product_type | string | Product stock type. `S` (own stock), `R` (from other suppliers) or `PO` (preorder)
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
wholesale[from] `(optional)` | numeric | Minimum purchase of products before wholesale applies
wholesale[to] `(optional)` | numeric | Maximum purchase of products after wholesale applies
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
variations[stock] `(optional)` | string | Product variation stock status. Required if `product_type: R or PO`. Available values: `Y` (in stock) or `N` (out of stock)
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
warehouse_id `(optional)` | integer | Variant warehouse ID taken from [Get Warehouse](/#get-warehouses)
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
Get minimum purchase of products before wholesale applies

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
product_type | string | Product stock type. `S` (own stock), `R` (from other suppliers) or `PO` (preorder)
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
from | numeric | Minimum purchase of products before wholesale applies
to | numeric | Maximum purchase of products after wholesale applies
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
stock `(optional)` | string | Product variation stock status. Required if `product_type: R or PO`. Available values: `Y` (in stock) or `N` (out of stock)
stock_quantity `(optional)` | integer | Product variation stock quantity. Required if `product_type: S`. Min 0

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
  "response": "Success",
  "message": "Success, your product data will be sent to juragan@ngorder.id soon"
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
corporate_id `(optional)` | string | Corporate ID. Required if `bank_type` is a business bank

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
corporate_id `(optional)` | string | Corporate ID. Required if `bank_type` is a business bank

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
      "phone": "08123456789",
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
      "phone": "08123456789",
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
        "next": "https://api.ngorder.id/api/open/expedition/active?pagination_offset=2"
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
        "logo_url": "https://cdn.shipper.cloud/logistic/small/SAP.png",
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
        "logo_url": "https://cdn.shipper.cloud/logistic/small/SAP.png",
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





# Promo
## Search Products Available
> Example request:

```json
```

> Example response:

```json
```
Search for available products to add to the promo.

### Endpoint
`GET https://api.ngorder.id/api/open/promo/product`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword | string | Product name to look for. Min: 3. Max: 50
type | string | Promo type. Available values: `PRODUCT` or `EXPEDITION`
id `(optional)` | string | Promo ID taken from [Get Promos](/#get-promos). Fill this if you want to check a certain promo
start_date `(optional)` | string | Start date range to search for promo. Format `yyyy-mm-dd`
end_date `(optional)` | string | End date range to search for promo. Format `yyyy-mm-dd`
couriers `(optional)` | integer | Couriers ID taken from [Get Expeditions](/#get-expeditions)
group | string | Promo group. Available values: `PROMO` or `COUPON`
per_page `(optional)` | integer | Data per page. Default `10`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default `1`






## Create a Promo
> Example request:

```json
{
  "type": "PRODUCT",
  "group": "PROMO",
  "name": "Testing",
  "coupon_code": "",
  "start_date": "2021-07-06 09:19",
  "end_date": "2021-07-06 23:19",
  "discount": {
    "type": "PERCENTAGE",
    "amount": 5,
    "max_nominal": 5000
  },
  "limits": {
    "usage_per_customer": "UNLIMITED",
    "promo_limit": 5,
    "minimum_product": null,
    "minimum_transaction": null
  },
  "is_active": true,
  "customer_categories": [
    "N",
    "Y",
    "D"
  ],
  "all_products": true,
  "selected_items": {
    "products": [
      1,
      2,
      3
    ],
    "platforms": [
      "ORDER_APP",
      "PRIVOR"
    ],
    "couriers": [
      1,
      2,
      3
    ]
  }
}
```

> Example response:

```json
{
  "response": "Success",
  "message": "data has been successfully saved",
  "data": {
    "promo_id": 123
  }
}
```
Create a promo.

### Endpoint
`POST https://api.ngorder.id/api/open/promo`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
group | string | Promo group. Available values: `PROMO` or `COUPON`.
type | string | Promo type. Available values: `PRODUCT` or `EXPEDITION`
name | string | Promo name
coupon_code `(optional)` | string | Coupon code. Required if `group: COUPON`
start_date | string | Promo start date. Format `yyyy-mm-dd hh:mm`. Cannot be less than the current date
end_date | string | Promo end date. Format `yyyy-mm-dd hh:mm`.
discount | array | Discount detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>type</td><td>`string` Discount type. Available values: `PERCENTAGE` or `NOMINAL`</td></tr><tr><td>amount</td><td>`integer` Discount amount. Either nominal or percentage discount</td></tr><tr><td>max_nominal `(optional)`</td><td>`integer` Maximum discount amount applied</td></tr></table>
limits | array | Limits detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>usage_per_customer `(optional)`</td><td> `string` Usage per customer limit. Available values: `1 to 9` or leave empty for unlimited usage</td></tr><tr><td>promo_limit `(optional)`</td><td>`string` Total promo quota. Leave empty if unlimited</td></tr><tr><td>minimum_product `(optional)`</td><td>`integer` Minimum purchase of products before this promo applies</td></tr><tr><td>minimum_transaction `optional`</td><td>`integer` Minimum cost before this promo applies</td></tr></table>
is_active | boolean | Promo activation status
customer_categories | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)
all_products | boolean | Promo applies to all product
selected_items | array | Selected items detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>products `optional`</td><td>`[]integer` List of products ID taken from [Get Products](/#get-products). Required if`all_products: false` and `type: PRODUCT`</td></tr><tr><td>platforms</td><td>`[]string` List of platforms. Available values:`ORDER_APP`, `PROMO`, `PRIVOR`, `STOREFRONT` or `QUICK_ORDER`</td></tr><tr><td>couriers</td><td>`[]string` List of couriers ID taken from [Get Expeditions](/#get-expeditions)</td></tr></table>







## Get Promos
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "name": "Kupon KUPON50",
      "is_active": true,
      "total_selected_items": "semua",
      "type": "EXPEDITION",
      "group": "COUPON",
      "start_date": "2021-07-01 00:00:00",
      "end_date": "2021-07-31 23:59:59"
    },
    {
      "id": 2,
      "name": "Promo Awal Bulan",
      "is_active": true,
      "total_selected_items": "All",
      "type": "PRODUCT",
      "group": "PROMO",
      "start_date": "2021-07-01 00:00:00",
      "end_date": "2021-07-07 23:59:59"
    }
  ],
  "meta": {
    "pagination": {
      "total": 21,
      "count": 5,
      "per_page": 5,
      "current_page": 1,
      "total_pages": 5,
      "links": {
        "next": "https://api.ngorder.id/api/open/promo?pagination_offset=2"
      }
    }
  }
}
```
Get list of promos you have.

### Endpoint
`GET https://api.ngorder.id/api/open/promo`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | Promo name or coupon code to look for. Max: `20`
type `(optional)` | string | Promo type. Available values: `PRODUCT` or `EXPEDITION`
is_active | boolean | Promo activation status
per_page `(optional)` | integer | Data per page. Default `10`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default `1`









## Get Promo Detail
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "id": 683,
    "group": "PROMO",
    "name": "merdeka",
    "coupon_code": "ONGKIR5000",
    "type": "EXPEDITION",
    "start_date": "2020-04-03 00:00:00",
    "end_date": null,
    "is_active": true,
    "discount": {
      "type": "NOMINAL",
      "amount": 5000,
      "max_nominal": 5000
    },
    "limits": {
      "usage_per_customer": "UNLIMITED",
      "promo_limit": null,
      "minimum_product": null,
      "minimum_transaction": 0
    },
    "all_products": false,
    "selected_items": {
      "products": [
        {
          "id": 1053,
          "produk": "Produk",
          "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/7/products/test-json-image-1611709513144.jpg",
          "thumbnail": "https://cepat.b-cdn.net/7/products/test-json-image-1611709513144.jpg"
        }
      ],
      "couriers": [
        {
          "id": 1,
          "logistic_name": "JNE",
          "rate_name": "REG",
          "logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/jne.png"
        },
        {
          "id": 2,
          "logistic_name": "JNE",
          "rate_name": "YES",
          "logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/jne.png"
        },
        {
          "id": 3,
          "logistic_name": "JNE",
          "rate_name": "OKE",
          "logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/jne.png"
        },
        {
          "id": 4,
          "logistic_name": "JNE",
          "rate_name": "CTC",
          "logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/jne.png"
        }
      ],
      "platforms": [
        "ORDER_APP",
        "PRIVOR"
      ]
    },
    "customer_categories": [
      {
        "code": "N",
        "name": "Customer",
        "selected": true
      },
      {
        "code": "Y",
        "name": "Reseller",
        "selected": true
      },
      {
        "code": "D",
        "name": "Dropshipper",
        "selected": true
      },
      {
        "code": "1",
        "name": "Pelanggan Tetap",
        "selected": true
      },
      {
        "code": "2",
        "name": "Harga Teman",
        "selected": true
      }
    ]
  }
}
```
Get detailed promo info.

### Endpoint
`GET https://api.ngorder.id/api/open/promo/{id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Promo ID taken from [Get Promos](/#get-promos)








## Update Promo
> Example request:

```json
{
  "id": 123,
  "type": "PRODUCT",
  "group": "PROMO",
  "name": "Testing",
  "coupon_code": "",
  "start_date": "2021-07-06 09:19",
  "end_date": "2021-07-06 23:19",
  "discount": {
    "type": "PERCENTAGE",
    "amount": 5,
    "max_nominal": 5000
  },
  "limits": {
    "usage_per_customer": "UNLIMITED",
    "promo_limit": 5,
    "minimum_product": 10,
    "minimum_transaction": 10000
  },
  "is_active": true,
  "customer_categories": [
    "N",
    "Y",
    "D"
  ],
  "all_products": true,
  "selected_items": {
    "products": [
      1,
      2,
      3
    ],
    "platforms": [
      "ORDER_APP",
      "PRIVOR"
    ],
    "couriers": [
      1,
      2,
      3
    ]
  }
}
```

> Example response:

```json
{
  "response": "Success",
  "message": "data has been successfully saved",
  "data": {
    "promo_id": 123
  }
}
```
Update a promo.

### Endpoint
`PATCH https://api.ngorder.id/api/open/promo`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Promo ID taken from [Get Promos](/#get-promos)
group | string | Promo group. Available values: `PROMO` or `COUPON`.
type | string | Promo type. Available values: `PRODUCT` or `EXPEDITION`
name | string | Promo name
coupon_code `(optional)` | string | Coupon code. Required if `group: COUPON`
start_date | string | Promo start date. Format `yyyy-mm-dd hh:mm`. Cannot be less than the current date
end_date | string | Promo end date. Format `yyyy-mm-dd hh:mm`.
limits | array | Limits detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>usage_per_customer `(optional)`</td><td> `string` Usage per customer limit. Available values: `1 to 9` or leave empty for unlimited usage</td></tr><tr><td>promo_limit `(optional)`</td><td>`string` Total promo quota. Leave empty if unlimited</td></tr><tr><td>minimum_product `(optional)`</td><td>`integer` Minimum purchase of products before this promo applies</td></tr><tr><td>minimum_transaction `optional`</td><td>`integer` Minimum cost before this promo applies</td></tr></table>
is_active | boolean | Promo activation status
customer_categories | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)
all_products | boolean | Promo applies to all product
selected_items | array | Selected items detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>products `optional`</td><td>`[]integer` List of products ID taken from [Get Products](/#get-products). Required if`all_products: false` and `type: PRODUCT`</td></tr><tr><td>platforms</td><td>`[]string` List of platforms. Available values:`ORDER_APP`, `PROMO`, `PRIVOR`, `STOREFRONT` or `QUICK_ORDER`</td></tr><tr><td>couriers</td><td>`[]string` List of couriers ID taken from [Get Expeditions](/#get-expeditions)</td></tr></table>





## Delete Promo
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "Data has been deleted",
  "data": null
}
```
Delete a promo.

### Endpoint
`DELETE https://api.ngorder.id/api/open/promo/{id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
Promo ID taken from [Get Promos](/#get-promos)







## template
> Example request:

```json
```

> Example response:

```json
```
m

### Endpoint
`GET https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------




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
products | array | Product variants detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>id</td><td>`integer` Product variant ID</td></tr><tr><td>qty</td><td>`integer` Product quantity</td></tr><tr><td>warehouse_id `(optional)`</td><td>`integer` Product variant warehouse ID taken from [Get Warehouses](#get-warehouses)</td></tr><tr><td>product_status</td><td>`string` Product stock type `S` (own stock), `R` (from other suppliers) or `PO` (preorder)</td></tr><tr><td>type `(optional)`</td><td>`string` Product discount type. Available values: `NOMINAL` or `PERCENTAGE`</td></tr><tr><td>percentage `(optional)`</td><td>`integer` Discount percentage. Required if `type: PERCENTAGE`</td></tr><tr><td>nominal `(optional)`</td><td>`integer` Discount nominal. Required if `type: NOMINAL`</td></tr><tr><td>flag `(optional)`</td><td>`string` Product update status. Available values: `EDIT`, `NEW` or `DELETE`</td></tr><tr><td>discount_promo `(optional)`</td><td>`integer` Product promo discount nominal. If this filled product discount will be removed</td></tr><tr><td>promo_id `(optional)`</td><td>`integer` Promo ID</td></tr></table>
expedition | array | Expedition detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>id</td><td>`integer` Expedition ID</td></tr><tr><td>rate</td><td>`integer` Expedition cost</td></tr><tr><td>name</td><td>`string` Expedition name</td></tr><tr><td>auto_pickup</td><td>`boolean` Expedition auto pickup status</td></tr><tr><td>discount_promo `(optional)`</td><td>`integer` Expedition discount nominal</td></tr><tr><td>promo `(optional)`</td><td>`array` Promo detail from [Product Variants](/#get-product-variations)</td></tr></table>
payment | array | Payment detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>status</td><td>`string` Payment status. Available values: `PAID`, `INSTALLMENT` or `UNPAID`</td></tr><tr><td> date `(optional)` </td><td>`string` Payment date. Required if `status: PAID or INSTALLMENT`. Format `yyy-mm-dd`</td></tr><tr><td>bank_id `(optional)` </td><td>`integer` Bank ID. Required if `status: PAID or INSTALLMENT` taken from [Bank Accounts](/#get-shop-bank-accounts)</td></tr><tr><td>amount</td><td>`integer` Payment amount. Required if `status: PAID or INSTALLMENT`</td></tr><tr><td>cost_of_goods_sales `(optional)` </td><td>`integer` Cost to be paid to the supplier. Required if `product_status: R` (see [Create a Product](/#create-product))</td></tr></table>
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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID taken from [Create Order](/#create-order)
awb_number | string | Air waybill number


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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Keyword to look for
payment_status `(optional)` | string | Filter by payment status. Available values: `UNPAID`, `PAID` or `INSTALLMENT`
order_progress_status | string | Filter by order progress status. Available values: `UNPAID`, `NO AWB`, `ON PROCESS`, `DELIVERED`, `UNPROCESSED` or `INSTALLMENT`
order_category `(optional)` | string | Source of created order. Available values: `APP`, `PRIVOR`, `STORE_FRONT`, `SHOPEE`, `QUICK_ORDER` or `UNCATEGORIZED`
order_source_id `(optional)` | integer | Sales channel ID taken from [Order Source](/#get-order-sources)
type `(optional)` | string | Order type. Available values: `ORDER_ID`, `CUSTOMER_NAME`, `AWB_NUMBER`, `CUSTOMER_PHONE`, `SHOPEE_INVOICE`, `PRODUCT_NAME`, `SKU` or `SHIPPER_TRACKING`
order_by `(optional)` | string | Order the data. Available values: `ORDER_DATE` or `PAYMENT_DATE`. Default value: `ORDER_DATE`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`. Default value: 30 days ago
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`. Default value: today
user_id `(optional)` | integer | The ID of admin who made this order
bank_id `(optional)` | integer | Bank ID taken from [Bank Accounts](/#get-shop-bank-accounts)
warehouse_id  `(optional)` |  integer | Product variant warehouse ID taken from [Get Warehouses](#get-warehouses)
customer_category_code `(optional)` | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)
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
token | string | Bearer token

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




## Get Single Order Detail
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "order_id": 1352,
    "po_number": 10746,
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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID


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
token | string | Bearer token

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
token | string | Bearer token

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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
payment_status `(optional)` | string | Order payment status. Available status: `UNPAID`, `PAID` or `INSTALLMENT`
order_progress_status `(optional)` | Order progress status. Available status: `UNPAID`, `NO AWB`, `ON PROCESS`, `DELIVERED`, `UNPROCESSED` or `INSTALLMENT`
order_category `(optional)` | string | Source of created order. Available values: `APP`, `PRIVOR`, `STORE_FRONT`, `SHOPEE`, `QUICK_ORDER` or `UNCATEGORIZED`
order_source_id `(optional)` | integer | Sales channel ID taken from [Order Source](/#get-order-sources)
type `(optional)` | string | Filter type. Available values: `ORDER_ID`, `CUSTOMER_NAME`, `AWB_NUMBER`, `CUSTOMER_PHONE`, `SHOPEE_INVOICE`, `PRODUCT_NAME`, `SKU` or `SHIPPER_TRACKING`
keyword `(optional)` | string | Keyword to look for
order_by `(optional)` | string | Order the data. Available values: `ORDER_DATE` or `PAYMENT_DATE`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`. Default values: 30 days ago
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`. Default values: today
user_id `(optional)` | integer | User ID
bank_id `(optional)` | integer | Bank ID taken from [Bank Accounts](/#get-shop-bank-accounts)
warehouse_id  `(optional)` |  integer | Product variant warehouse ID taken from [Get Warehouses](#get-warehouses)
customer_category_code `(optional)` | integer | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)
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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID taken from [Get Orders](/#get-orders)
payment | array | Payment details <table><tr><th>Key</th><th>Value</th></tr><tr><td>status</td><td>`integer` Payment status. Available values: `PAID` or `INSTALLMENT`</td></tr><tr><td>date</td><td>`string` Payment date. Format `yyyy-mm-dd`</td></tr><tr><td>bank_id</td><td>`integer` Bank ID taken from [Bank Accounts](/#get-shop-bank-accounts)</td></tr><tr><td>amount `(optional)`</td><td>`integer` Payment amount. Required if `status: INSTALLMENT`</td></tr><tr><td>cost_of_goods_sales</td><td>`integer` Cost to be paid to the supplier. Required if `product_status: R` (see [Create a Product](/#create-product))</td></tr></table>


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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
order_id | integer | Order ID
customer_sender_id | integer |  Customer sender ID taken from [Customer](/#customer)
customer_receiver_id | integer | Customer receiver ID taken from [Customer](/#customer)
supplier_id | integer | Supplier ID taken from [Supplier](/#supplier)
order_source_id `(optional)` | integer | Order source ID taken from [Order Source](/#order-source)
note `(optional)` | string | Note for the order
is_print | boolean | Order print status
products | array | Product variants detail


expedition | array | Expedition detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>id</td><td>`integer` Expedition ID</td></tr><tr><td>rate</td><td>`integer` Expedition cost</td></tr><tr><td>name</td><td>`string` Expedition name</td></tr><tr><td>auto_pickup</td><td>`boolean` Expedition auto pickup status</td></tr><tr><td>discount_promo `(optional)`</td><td>`integer` Expedition discount nominal</td></tr><tr><td>promo `(optional)`</td><td>`array` Promo detail from [Product Variants](/#get-product-variations)</td></tr></table>
payment | array | Payment detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>status</td><td>`string` Payment status. Available values: `PAID`, `INSTALLMENT` or `UNPAID`</td></tr><tr><td> date `(optional)` </td><td>`string` Payment date. Required if `status: PAID or INSTALLMENT`. Format `yyy-mm-dd`</td></tr><tr><td>bank_id `(optional)` </td><td>`integer` Bank ID. Required if `status: PAID or INSTALLMENT` taken from [Bank Accounts](/#get-shop-bank-accounts)</td></tr><tr><td>amount</td><td>`integer` Payment amount. Required if `status: PAID or INSTALLMENT`</td></tr><tr><td>cost_of_goods_sales `(optional)` </td><td>`integer` Cost to be paid to the supplier. Required if `product_status: R` (see [Create a Product](/#create-product))</td></tr></table>
order_cost `(optional)` | array | Other cost detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>name</td><td>`string` Order cost name</td></tr><tr><td>category</td><td>`string` Cost category. Available values: `DISCOUNT`, `OTHER COST` or `INSURANCE`</td></tr><tr><td>type</td><td>`string` Cost type. Available values: `NOMINAL` or `PERCENTAGE`</td></tr><tr><td>percentage `(optional)` </td><td>`integer` Order cost percentage. Required if `type: PERCENTAGE`</td></tr><tr><td>nominal `(optional)` </td><td>`integer` Order cost nominal. Required if `type: NOMINAL`</td></tr></table>
awb_number `(optional)` | string | Air waybill number
send_sms `(optional)` | boolean | SMS status. Default value: `false`
marketplace_awb `(optional)` | string | Marketplace air waybill
source | string | Source platform. Available values: `MOBILE` or `WEB`






## template
> Example request:

```json
```

> Example response:

```json
```
m

### Endpoint
`GET https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------


## Order Source -opt
## Order Cost -opt
## Order CRUD
## Setting

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
token | string | Bearer token

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
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
payment_id | integer | Payment ID taken from [Get Privor Orders](/#get-orders-2)






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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Payment ID taken from [Get Privor Orders](/#get-orders-2)
orders | array | Privor orders <table><tr><th>Key</th><th>Value</th></tr><tr><td>id</td><td>`integer` Privor order ID</td></tr><tr><td>action</td><td>`string` Confirmation action. Available values: `ACCEPT` or `REJECT`</td></tr></table>






# Setting Storefront Courier
## Get Active Couriers
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "Regular": [
      {
        "id": 1,
        "logistic_name": "JNE",
        "rate_name": "REG",
        "is_active": false
      },
      {
        "id": 8,
        "logistic_name": "RPX",
        "rate_name": "RGP",
        "is_active": true
      },
      {
        "id": 700,
        "logistic_name": "Tiki",
        "rate_name": "ECO",
        "is_active": true
      },
      {
        "id": 900,
        "logistic_name": "SAP",
        "rate_name": "UDRREG",
        "is_active": true
      },
      {
        "id": 902,
        "logistic_name": "SAP",
        "rate_name": "DRGREG",
        "is_active": true
      },
      {
        "id": 903,
        "logistic_name": "SiCepat",
        "rate_name": "SIUNT",
        "is_active": true
      },
      {
        "id": 915,
        "logistic_name": "J-Xpress",
        "rate_name": "Regular",
        "is_active": true
      },
      {
        "id": 921,
        "logistic_name": "iDExpress",
        "rate_name": "STD",
        "is_active": true
      }
    ],
    "Express": [
      {
        "id": 2,
        "logistic_name": "JNE",
        "rate_name": "YES",
        "is_active": false
      },
      {
        "id": 10,
        "logistic_name": "JNE",
        "rate_name": "CTCYES",
        "is_active": false
      },
      {
        "id": 11,
        "logistic_name": "RPX",
        "rate_name": "NDP",
        "is_active": true
      },
      {
        "id": 42,
        "logistic_name": "Lion Parcel",
        "rate_name": "ONEPACK",
        "is_active": true
      },
      {
        "id": 52,
        "logistic_name": "Tiki",
        "rate_name": "ONS",
        "is_active": true
      }
    ],
    "Trucking": [
      {
        "id": 363,
        "logistic_name": "Sicepat",
        "rate_name": "GOKIL",
        "is_active": false
      }
    ]
  }
}
```
Get list of account active couriers.

### Endpoint
`GET https://api.ngorder.id/api/open/setting/courier`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token








## Get Custom Couriers
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "name": "KURIR TOKO",
      "fee": 30000
    },
    {
      "id": 2,
      "name": "INDAH KARGO",
      "fee": 40000
    }
  ]
}
```
Get list of your shop custom couriers.

### Endpoint
`GET https://api.ngorder.id/api/open/setting/courier/custom`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token






## Update Courier Active Status
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "data has been successfully saved",
  "data": {
    "id": 1,
    "is_active": false
  }
}
```
Update courier activation status.

### Endpoint
`PATCH https://api.ngorder.id/api/open/setting/courier`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | string | Courier ID
is_active `(optional)` | boolean | Active status. Default value: `false`






## Update Couriers Active Status
> Example request:

```json
{
  "regular": [
    "4",
    "8",
    "15"
  ],
  "express": [
    "11",
    "42",
    "52",
    "56"
  ],
  "trucking": []
}
```

> Example response:

```json
{
  "response": "Success",
  "message": "data has been successfully saved",
  "data": {
    "regular": [
      "4",
      "8",
      "15"
    ],
    "express": [
      "11",
      "42",
      "52",
      "56"
    ],
    "trucking": []
  }
}
```
Update active status on multiple couriers. All IDs are taken from [Get Expeditions](/#get-expeditions)

### Endpoint
`PATCH https://api.ngorder.id/api/open/setting/courier/all`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
regular `(optional)` | []string | Regular couriers ID 
express `(optional)` | []string | Express couriers ID
trucking `(optional)` | []string | Trucking couriers ID





## Update Custom Courier
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 7
  }
}
```
Update custom courier details.

### Endpoint
`PATCH https://api.ngorder.id/api/open/setting/courier/custom`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Custom courier ID taken from [Custom Couriers](/#get-custom-couriers)
name | string | Custom courier name
fee | integer | Custom courier cost






## Delete Custom Courier
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "Data has been deleted",
  "data": {
    "id": 7
  }
}
```
Delete a custom courier.

### Endpoint
`DELETE https://api.ngorder.id/api/open/setting/courier/custom/{id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Custom courier ID taken from [Custom Couriers](/#get-custom-couriers)








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
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
order_id | integer | Order ID taken from [Get Orders](/#get-orders)







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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
pickup_request | array | Order data <table><tr><th>Key</th><th>Value</th></tr><tr><td>id</td><td>`integer` Order ID taken from [Get Orders](/#get-orders)</td></tr><tr><td>service `(optional)`</td><td>`string` Shipment service. Available values: `PICKUP` or `DROP_OFF`. Default value: `PICKUP`</td></tr></table>





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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID taken from [Get Orders](/#get-orders)
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
token | string | Bearer token






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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
courier `(optional)` | string | Expedition name taken from [Get Active COD Couriers](/#get-active-cod-couriers)
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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
courier `(optional)` | string | Expedition name taken from [Get Active COD Couriers](/#get-active-cod-couriers)
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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
courier `(optional)` | string | Expedition name taken from [Get Active COD Couriers](/#get-active-cod-couriers)
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
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Invoice ID taken from [Get Shipment Invoices](/#get-shipment-invoices)







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
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
invoice_id | string | Invoice ID taken from [Get Shipment Invoices](/#get-shipment-invoices)







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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
courier `(optional)` | string | Expedition name taken from [Get Active COD Couriers](/#get-active-cod-couriers)
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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Keyword to look for
courier `(optional)` | string | Expedition name taken from [Get Active COD Couriers](/#get-active-cod-couriers)
status `(optional)` | string | Order progress. Available values: `READY_TO_SHIP`, `PICKUP_REQUEST`, `UNPICK`, `ON_PROCESS`, `DELIVERED`, `RETURNED`, `LOST`, `INVALID`, `SHIPMENT_PROBLEM` or `DROPOFF`. Default value: `READY_TO_SHIP`
type `(optional)` | string | Filter by type. Available values: `ORDER_ID`, `CUSTOMER_NAME` or `AWB_NUMBER`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`. Default value: today
cod_status `(optional)` | string | Shipment COD status. Available values: `NON_COD` or `COD`
supplier_id `optional` | integer | Supplier ID taken from [Get Suppliers](/#get-suppliers)
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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Keyword to look for
courier `(optional)` | string | Expedition name taken from [Get Active COD Couriers](/#get-active-cod-couriers)
status `(optional)` | string | Order progress. Available values: `READY_TO_SHIP`, `PICKUP_REQUEST`, `UNPICK`, `ON_PROCESS`, `DELIVERED`, `RETURNED`, `LOST`, `INVALID`, `SHIPMENT_PROBLEM` or `DROPOFF`. Default value: `READY_TO_SHIP`
type `(optional)` | string | Filter by type. Available values: `ORDER_ID`, `CUSTOMER_NAME` or `AWB_NUMBER`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`. Default value: today
cod_status `(optional)` | string | Shipment COD status. Available values: `NON_COD` or `COD`
supplier_id `optional` | integer | Supplier ID taken from [Get Suppliers](/#get-suppliers)








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
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
order_id | integer | Order ID taken from [Get Orders](/#get-orders)








# Setting Payment Fee
## Create an Admin Fee
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 262,
    "nominal": "1200",
    "category_code": "1"
  }
}
```
Create an admin fee.

### Endpoint
`POST https://api.ngorder.id/api/open/setting/payment/admin-fee`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
nominal | integer | Admin fee nominal. Max `4500`
catgory_code | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)







## Get Admin Fees
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "id": 103,
      "nominal": 1500,
      "customer_category": {
        "code": "Y",
        "name": "Reseller"
      }
    },
    {
      "id": 104,
      "nominal": 4500,
      "customer_category": {
        "code": "N",
        "name": "Pelanggan"
      }
    },
    {
      "id": 115,
      "nominal": 2000,
      "customer_category": {
        "code": "D",
        "name": "Dropshipper"
      }
    },
    {
      "id": 262,
      "nominal": 1000,
      "customer_category": {
        "code": "1",
        "name": "Harga Teman"
      }
    }
  ]
}
```
Get list of admin fees.

### Endpoint
`GET https://api.ngorder.id/api/open/setting/payment/admin-fee`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token







## Update an Admin Fee
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 262,
    "nominal": "1200",
    "category_code": "1"
  }
}
```
Update an admin fee.

### Endpoint
`PATCH https://api.ngorder.id/api/open/setting/payment/admin-fee`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Admin fee ID taken from [Get Admin Fees](/#get-admin-fees)
nominal | integer | Admin fee nominal. Max `4500`
catgory_code | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [Customer Categories](/#get-categories-2)







## Get Xendit Data
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "xendit_key": "xnd_development_OImJfL8g1bHnM84L7EcTDeWY4OmqNUolCC2RxnmLWrelCwZhg",
    "is_xendit_active": true,
    "bank_support": [
      {
        "id": 26137,
        "name": "Mandiri Virtual Accounts",
        "holder_name": "NgorderID",
        "bank_number": null,
        "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/mandiri.png"
      },
      {
        "id": 26206,
        "name": "BNI Virtual Accounts",
        "holder_name": "NgorderID",
        "bank_number": null,
        "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bni.png"
      },
      {
        "id": 26207,
        "name": "Permata Virtual Accounts",
        "holder_name": "NgorderID",
        "bank_number": null,
        "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/permata.png"
      },
      {
        "id": 26208,
        "name": "BRI Virtual Accounts",
        "holder_name": "NgorderID",
        "bank_number": null,
        "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bri.png"
      }
    ]
  }
}
```
Get detailed Xendit data.

### Endpoint
`GET https://api.ngorder.id/api/open/setting/payment/xendit`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token







## Update Xendit Key
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "Payment settings were successfully updated",
  "data": {
    "xendit_key": "xnd_development_OImJfL8g1bHnM84L7EcTDeWY4OmqNUolCC2RxnmLWrelCwZhg"
  }
}
```
Update Xendit key.

### Endpoint
`PATCH https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
xendit_key | string | Xendit key taken from [Get Xendit Data](/#get-xendit-data)








# Payment
## Get Payment List
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "id": 1457,
      "transaction_number": "#INV1457",
      "type": {
        "id": "1",
        "status": "+"
      },
      "date": "2021-03-24 13:32:24",
      "title": "Pembayaran Order",
      "description": "Pembayaran order #12027 menggunakan Saldo Orderpay dari canceled order",
      "nominal": 167000
    },
    {
      "id": 1418,
      "transaction_number": "#INV1418",
      "type": {
        "id": "1",
        "status": "+"
      },
      "date": "2021-03-15 14:27:46",
      "title": "Pembayaran Order",
      "description": "Pembayaran order #12028 menggunakan Saldo Orderpay dari canceled order",
      "nominal": 167000
    }
  ],
  "meta": {
    "pagination": {
      "total": 15,
      "count": 2,
      "per_page": 2,
      "current_page": 1,
      "total_pages": 8,
      "links": {
        "next": "https://api.ngorder.id/api/open/payment?start_date=2021-01-31&end_date=2021-04-01&per_page=2&pagination_offset=2"
      }
    }
  }
}
```
Get list of payments.

### Endpoint
`GET https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
payment_type `(optional)` | string | Payment type. Available values: `ORDER_PAY` or `PAYMENT_GATEWAY`. Default value: `ORDER_PAY`
funds `(optional)` | string | Fund status. Available values: `OUTGOING` or `INCOMING`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`. Default value: start date of current month.
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`. Default value: today
per_page `(optional)` | integer | Data per page. Default value: `10`
pagination_offset `(optional)` | integer | Page number. Default value: `1`







## Get OrderPay Balance
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "total": 13484522,
    "withdrawal_allowed": 7813017,
    "onhold_total": 5671505,
    "balance_onhold": 4928504,
    "withdrawal_onhold": 743001
  }
}
```
Get OrderPay balance on your account.

### Endpoint
`GET https://api.ngorder.id/api/open/payment/orderpay-balance`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token










## Get Xendit Balance
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "balance": 13484522
  }
}
```
Get Xendit balance on your account.

### Endpoint
`GET https://api.ngorder.id/api/open/payment/xendit/balance`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token





## Withdraw
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "Withdrawal request is successful, we will process it soon"
}
```
Withdrawal.

### Endpoint
`POST https://api.ngorder.id/api/open/payment/withdraw`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
xendit_bank_id | integer | Bank ID taken from [Xendit Master Data](/#get-xendit-master-data)
nominal | integer | Withdrawal amount. Min Rp50.000. The admin fee of Rp45.000 will be automatically added to the final nominal.
holder_name | string | Holder name
account_number | integer | Account number







# Expense
## Create Expense
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 22,
    "title": "Cod Payment"
  }
}
```
Create an expense.

### Endpoint
`POST https://api.ngorder.id/api/open/expense`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
title | string | Expense title. Max `100`
nominal | integer | Expense nominal
note | string | Expense note
qty `(optional)` | integer | Expense quantity. Default value: `1`
date `(optional)` | string | Expense date. Format `yyy-mm-dd`. Default value: today





## Get Expenses
> Example request:

```json
```

> Example response:

```json
```
Get all expenses.

### Endpoint
`GET https://api.ngorder.id/api/open/expense`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | integer | Filter the data. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
per_page `(optional)` | integer | Data per page. Default value: `10`
pagination_offset `(optional)` | integer | Page number. Default value: `1`





## Download Expenses Data
> Example request:

```json
```

> Example response:

```json
```
Download expense data as Excel.

### Endpoint
`GET https://api.ngorder.id/api/open/expense/download`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | integer | Filter the data. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`



## Update Expense
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "data": {
    "id": 22,
    "title": "Cod Payment"
  }
}
```
Update an expense.

### Endpoint
`PATCH https://api.ngorder.id/api/open/expense`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Expense ID taken from [Get Expenses](/#get-expenses)
title | string | Expense title. Max `100`
nominal | integer | Expense nominal
note | string | Expense note
qty `(optional)` | integer | Expense quantity. Default value: `1`
date `(optional)` | string | Expense date. Format `yyy-mm-dd`. Default value: today





## Delete Expense
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "Data has been deleted",
  "data": {
    "id": 22
  }
}
```
Delete an expense

### Endpoint
`DELETE https://api.ngorder.id/api/open/expense/{id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Expense ID taken from [Get Expenses](/#get-expenses)




# Report
## Get Report
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "net_sales": {
      "nominal": 4895064,
      "percentage": 72
    },
    "gross_profit": {
      "nominal": 2380620,
      "percentage": 680
    },
    "gross_sales": {
      "nominal": 6072064,
      "unpaid": "Rp0"
    },
    "net_profit": {
      "nominal": 2380620,
      "percentage": 680
    },
    "expense": {
      "nominal": 0,
      "percentage": 0
    },
    "discount": 0,
    "postage": 1177000,
    "order_cost": 0,
    "product": {
      "total_stock": 193573,
      "assets": 2241653850
    },
    "shopee_active": true,
    "shopee": {
      "escrow_expense": null,
      "escrow_revenue": null,
      "total_amount": null,
      "total_escrow": null
    },
    "supplier_pay": {
      "show": true,
      "nominal": 0
    }
  }
}
```
Get report.

### Endpoint
`GET https://api.ngorder.id/api/open/report`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | integer | Filter the data. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`



## Get Detailed Report
> Example request:

```json
```

> Example response:

```json
{
  "by_source": [
    {
      "name": "App Dashboard",
      "value": 2220600
    },
    {
      "name": "Storefront",
      "value": 117998
    },
    {
      "name": "Guest Order",
      "value": 10
    }
  ],
  "by_admin": [
    {
      "user_id": 5,
      "name": "Tusfendi",
      "value": 2220600
    },
    {
      "user_id": 0,
      "name": "Uncategorized",
      "value": 118008
    }
  ]
}
```
Get detailed report.

### Endpoint
`GET https://api.ngorder.id/api/open/report/{group}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
group | string | Data group. Available values: `gross-sales`, `net-sales` or `gross-profit`

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | integer | Filter the data. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`



## Get Bank Acount Report
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "id": 847,
      "bank": "BCA",
      "holder_name": "Adina",
      "bank_number": "12345678",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bca.png",
      "nominal": 2413000,
      "idr": "Rp2.413.000"
    },
    {
      "id": 26211,
      "bank": "Srono",
      "holder_name": "Tusfendi",
      "bank_number": "12345678",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/other.png",
      "nominal": 1500000,
      "idr": "Rp1.500.000"
    }
  ]
}
```
Get bank account report.

### Endpoint
`GET https://api.ngorder.id/api/open/report/bank`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | integer | Filter the data. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`




## Get Sales Chart
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "date": "1",
      "amount": 1680000
    },
    {
      "date": "2",
      "amount": 480000
    },
    {
      "date": "3",
      "amount": 0
    },
    {
      "date": "4",
      "amount": 0
    },
    {
      "date": "5",
      "amount": 120000
    },
    {
      "date": "6",
      "amount": 0
    },
    {
      "date": "7",
      "amount": 0
    },
    {
      "date": "8",
      "amount": 0
    }
  ]
}
```
Get data for sales chart.

### Endpoint
`GET https://api.ngorder.id/api/open/report/chart/sales`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | integer | Filter the data. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`



## Get Profit Chart
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "date": "1",
      "net_sales": 1680000,
      "gross_profit": 280000
    },
    {
      "date": "2",
      "net_sales": 480000,
      "gross_profit": -432000
    },
    {
      "date": "3",
      "net_sales": 0,
      "gross_profit": 0
    },
    {
      "date": "4",
      "net_sales": 0,
      "gross_profit": 0
    },
    {
      "date": "5",
      "net_sales": 120000,
      "gross_profit": 20000
    },
    {
      "date": "6",
      "net_sales": 0,
      "gross_profit": 0
    },
    {
      "date": "7",
      "net_sales": 0,
      "gross_profit": 0
    },
    {
      "date": "8",
      "net_sales": 0,
      "gross_profit": 0
    },
    {
      "date": "9",
      "net_sales": 0,
      "gross_profit": 0
    }
  ]
}
```
Get data for profit chart.

### Endpoint
`GET https://api.ngorder.id/api/open/report/chart/profit`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | integer | Filter the data. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`




## Get Expedition Chart
> Example request:

```json
```

> Example response:

```json
{
  "total": 1633000,
  "data": [
    {
      "expedition_name": "JNE",
      "amount": 462000
    },
    {
      "expedition_name": "JNT",
      "amount": 42000
    },
    {
      "expedition_name": "SICEPAT",
      "amount": 49000
    },
    {
      "expedition_name": "SAP",
      "amount": 30000
    },
    {
      "expedition_name": "JX",
      "amount": 600000
    },
    {
      "expedition_name": "IDX",
      "amount": 450000
    }
  ]
}
```
Get data for profit chart.

### Endpoint
`GET https://api.ngorder.id/api/open/report/chart/expedition`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | integer | Filter the data. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`




# Analyzer
## Best Customer
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "name": "Tusfendi",
      "email": "t@gmail.com",
      "total_order": 10,
      "city": "Kabupaten Banyuwangi",
      "address": "JL. ABC, Kec. Srono, Kabupaten Banyuwangi, Jawa Timur",
      "category": "N",
      "category_name": "Pelanggan"
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
        "next": "https://api.ngorder.id/api/open/analyzer/customer?per_page=1&start_date=2021-03-01&end_date=2021-03-10&start_old=2021-02-01&end_old=2021-02-10&pagination_offset=2"
      }
    }
  }
}
```
Get best customers.

### Endpoint
`GET https://api.ngorder.id/api/open/analyzer/customer`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | integer | Filter the data. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
category `(optional)` | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)
order_by `(optional)` | string | Order the data. Available values: `TRANSACTION`, `SOLD_ITEMS`, `GROSS_SALES`, `NET_SALES` or `GROSS_PROFIT`. Just for owner's account. Default value: `TRANSACTION`
per_page `(optional)` | integer | Data per page. Default value: `100`
pagination_offset `(optional)` | integer | Page number. Default value: `1`




## Best Sales Product
> Example request:

```json
```

> Example response:

```json
```
Get best selling products.

### Endpoint
`GET https://api.ngorder.id/api/open/analyzer/sales`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
group_by | string | Group the data. Available values: `PRODUCT`, `SKU` or `CATEGORY`. Default value: `PRODUCT`
type `optional` | string | Filter the data by type. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
per_page `(optional)` | integer | Data per page. Default value: `100`
pagination_offset `(optional)` | integer | Page number. Default value: `1`





## Best Location
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "city": "Kabupaten Banyuwangi",
      "percentage": 86,
      "order": 19
    },
    {
      "city": "Kabupaten Wonogiri",
      "percentage": 14,
      "order": 3
    }
  ]
}
```
Get best location.

### Endpoint
`GET https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `optional` | string | Filter the data by type. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`






## Customer Chart
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "total_order": 24,
      "category": "N",
      "category_name": "Pelanggan"
    },
    {
      "total_order": 3,
      "category": "D",
      "category_name": "Dropshipper"
    }
  ]
}
```
Get data for customer chart.

### Endpoint
`GET https://api.ngorder.id/api/open/analyzer/customer/chart`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `optional` | string | Filter the data by type. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
category `(optional)` | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)
order_by `(optional)` | string | Order the data. Available values: `TRANSACTION`, `SOLD_ITEMS`, `GROSS_SALES`, `NET_SALES` or `GROSS_PROFIT`. Just for owner's account. Default value: `TRANSACTION`





## Analyzer Chart
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "id": 2,
      "day": "Senin",
      "total": 7
    },
    {
      "id": 3,
      "day": "Selasa",
      "total": 13
    },
    {
      "id": 6,
      "day": "Jumat",
      "total": 1
    },
    {
      "id": 1,
      "day": "Minggu",
      "total": 0
    },
    {
      "id": 4,
      "day": "Rabu",
      "total": 0
    },
    {
      "id": 5,
      "day": "Kamis",
      "total": 0
    },
    {
      "id": 7,
      "day": "Sabtu",
      "total": 0
    }
  ]
}
```
Get data for analyzer chart.

### Endpoint
`GET https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `optional` | string | Filter the data by type. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
per_page `(optional)` | integer | Data per page. Default value: `100`
pagination_offset `(optional)` | integer | Page number. Default value: `1`





## Download Best Sales Product

Download best sales product

### Endpoint
`GET https://api.ngorder.id/api/open/analyzer/sales/download`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Header
Parameter | Type | Description
--------- | ---- | -----------
group_by | string | Group the data. Available values: `PRODUCT`, `SKU` or `CATEGORY`. Default value: `PRODUCT`
type `optional` | string | Filter the data by type. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`




## Download Best Customer

Download best customer data as Excel.

### Endpoint
`GET https://api.ngorder.id/api/open/analyzer/customer/download`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `optional` | string | Filter the data by type. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
category `(optional)` | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](/#get-categories-2)
order_by `(optional)` | string | Order the data. Available values: `TRANSACTION`, `SOLD_ITEMS`, `GROSS_SALES`, `NET_SALES` or `GROSS_PROFIT`. Just for owner's account. Default value: `TRANSACTION`








# Notification
## Get Notifications
> Example request:

```json
```

> Example response:

```json
{
  "unread_count": 38,
  "data": [
    {
      "id": "09d93ba2-45ba-44ac-b1d7-0479346f1781",
      "title": "Orderan baru dari Storefront",
      "content": "<strong>Zonen</strong> memesan tas rampage UWU biru muda, sudah konfirmasi bayar <strong>Rp721.000</strong>, mohon segera konfirmasi pemesanan",
      "body": "Zonen memesan Tas Rampage biru muda, sudah konfirmasi bayar Rp721.000, mohon segera konfirmasi pemesanan",
      "icon": "https://sgp1.digitaloceanspaces.com/ngorder-1/icon/storefront.png",
      "web_path": "order/form_confirmation/1632919",
      "action": {
        "data_id": 1632919,
        "type": "confirm_order",
        "api_path": "/api/open/order/confirm"
      },
      "time_ago": "1 bulan yang lalu"
    },
    {
      "id": "caa3d67a-182e-4bb9-8495-c3d01da1acf9",
      "title": "Orderan baru dari Storefront",
      "content": "<strong>Naya Anindita</strong> memesan Kaos Polo L abu-abu, sudah konfirmasi bayar <strong>Rp57.280</strong>, mohon segera konfirmasi pemesanan",
      "body": "Naya Anindita memesan Kaos Polo L abu-abu, sudah konfirmasi bayar Rp57.280, mohon segera konfirmasi pemesanan",
      "icon": "https://sgp1.digitaloceanspaces.com/ngorder-1/icon/storefront.png",
      "web_path": "order/form_confirmation/1632818",
      "action": {
        "data_id": 1632818,
        "type": "confirm_order",
        "api_path": "/api/open/order/confirm"
      },
      "time_ago": "1 bulan yang lalu"
    }
  ],
  "meta": {
    "pagination": {
      "total": 42,
      "count": 2,
      "per_page": 20,
      "current_page": 3,
      "total_pages": 3,
      "links": {
        "previous": "https://api.ngorder.id/api/open/notification?pagination_offset=2"
      }
    }
  }
}
```
Get all notifications for selected type.

### Endpoint
`GET https://api.ngorder.id/api/open/notification`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | string | Notification type. Available values: `ACTIVITY` or `NEWS`. Default value: `ACTIVITY`
per_page `(optional)` | integer | Data per page. Default `20`
pagination_offset `(optional)` | integer | Page number. Default `1`





## Get Unread Count
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "activity": 390,
    "news": 43,
    "activity_display": "99+",
    "news_display": "43"
  }
}
```
Get unread notifications count.

### Endpoint
`GET https://api.ngorder.id/api/open/notification/unread`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token






## Push Device Token
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "token": "abcdefGHIJKL",
    "device": "Samsung S20+",
    "user_id": 51235
  }
}
```
Push device token.

### Endpoint
`POST https://api.ngorder.id/api/open/notification/token`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
token | integer | Device Firebase cloud messaging token






## Read Notifications
> Example request:

```json
```

> Example response:

```json
{
  "request_id": "6059a5b058d79",
  "response": "Success"
}
```
Mark notification as read.

### Endpoint
`POST https://api.ngorder.id/api/open/notification/read`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id `(optional)` | string | Notification ID taken from [Get Notifications](/#get-notifications)
type `(optional)` | string | Notification type. Available values: `ACTIVITY` or `NEWS`. Default value: `ACTIVITY`






# Billing
## Get Active Addons
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "sort": 1,
      "class": "app",
      "button_title": "Upgrade",
      "message": null,
      "sub_message": "Expired Pada Rabu, 26 Jan 2022",
      "active": true,
      "logo": "https://sgp1.digitaloceanspaces.com/icon/upgrade/app.png",
      "link": "https://app.ngorder.id/upgrade?app=platinum-12",
      "package": "App Platinum"
    },
    {
      "sort": 2,
      "class": "storefront",
      "button_title": "Perpanjang Sekarang",
      "message": null,
      "sub_message": "Layaran Expired",
      "active": true,
      "logo": "https://sgp1.digitaloceanspaces.com/icon/upgrade/storefront.svg",
      "link": "https://app.ngorder.id/upgrade?storefront=sf-pro",
      "package": "Storefront Pro"
    },
    {
      "sort": 3,
      "class": "shopee",
      "button_title": "Upgrade",
      "message": null,
      "sub_message": "Expired Pada Selasa, 6 Feb 2024",
      "active": true,
      "logo": "https://sgp1.digitaloceanspaces.com/icon/upgrade/shopee.svg",
      "link": "https://app.ngorder.id/upgrade?shopee=shopee-unlimited",
      "package": "Shopee Unlimited 6"
    },
    {
      "sort": 4,
      "class": "sms",
      "button_title": "Upgrade",
      "message": "Credit: 1245",
      "sub_message": "Expired Pada Minggu, 2 Jan 2022",
      "active": true,
      "logo": "https://sgp1.digitaloceanspaces.com/icon/upgrade/awb-notification.svg",
      "link": "https://app.ngorder.id/upgrade?sms=sms-1000",
      "package": "Notifikasi Resi"
    },
    {
      "sort": 5,
      "class": "mutation",
      "button_title": "Tambah Credit",
      "message": "Credit: 108000",
      "sub_message": null,
      "active": true,
      "logo": "https://sgp1.digitaloceanspaces.com/icon/upgrade/mutation.svg",
      "link": "https://app.ngorder.id/mutasi/credit",
      "package": "Mutasi Bank"
    },
    {
      "sort": 6,
      "class": "woowa",
      "button_title": "Upgrade",
      "message": null,
      "sub_message": "Expired Pada Kamis, 3 Nov 2022",
      "active": true,
      "logo": "https://sgp1.digitaloceanspaces.com/icon/upgrade/woowa.svg",
      "link": "https://app.ngorder.id/upgrade?woowa=woowa-economic",
      "package": "Woowa Economic"
    }
  ]
}
```
Get user active addons.

### Endpoint
`GET https://api.ngorder.id/api/open/billing/addons`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token





## Get Billing List
> Example request:

```json
```

> Example response:

```json
{
  "start_date": "2018-10-18",
  "end_date": "2021-06-14",
  "data": [
    {
      "id": 15408,
      "invoice": "INV-00007-5-220",
      "invoice_url": "https://app.ngorder.id/xendit/606d14d439ade3401b332af5",
      "services": [
        "Shopee Basic - 3 bulan"
      ],
      "created_at": "2021-04-07T02:11:32.000000Z",
      "payment_date": "2021-04-07T02:11:32.000000Z",
      "xendit_id": "606d14d439ade3401b332af5",
      "status": "EXPIRED",
      "amount": 323500,
      "received_amount": 0,
      "payment_method": "Virtual Account",
      "bank_image": null
    },
    {
      "id": 15329,
      "invoice": "INV-00007-5-219",
      "invoice_url": "https://app.ngorder.id/xendit/6064433a0a5cca4019b9a020",
      "services": [
        "Ngorder Premium - 1 th"
      ],
      "created_at": "2021-03-31T09:39:06.000000Z",
      "payment_date": "2021-03-31T09:39:06.000000Z",
      "xendit_id": "6064433a0a5cca4019b9a020",
      "status": "EXPIRED",
      "amount": 682500,
      "received_amount": 0,
      "payment_method": "Virtual Account",
      "bank_image": null
    }
  ],
  "meta": {
    "pagination": {
      "total": 220,
      "count": 2,
      "per_page": 2,
      "current_page": 1,
      "total_pages": 110,
      "links": {
        "next": "https://api.ngorder.id//api/open/billing?pagination_offset=2"
      }
    }
  }
}
```
Get user billing histories.

### Endpoint
`GET https://api.ngorder.id/api/open/billing`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
per_page `(optional)` | integer | Data per page. Default `50`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default `1`





## Download Invoice
> Example request:

```json
```
Download invoice as PDF

### Endpoint
`GET https://api.ngorder.id/api/open/billing/{id}/download`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Invoice ID







# Woowa Customer
## Get Template
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "id": 23,
      "type": "CUSTOM_NOTIFICATION",
      "template": "Maaf toko {%shopname%} libur,\nuntuk semua chat akan dibalas saat toko kembali aktif. "
    },
    {
      "id": 27,
      "type": "PROMO",
      "template": "Halo kak {%buyer%}, sedang ada promo 35% untuk semua product dan varian"
    }
  ]
}
```
Get message templates.

### Endpoint
`GET https://api.ngorder.id/api/open/woowa/customer`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token




## Send Bulk Message
> Example request:

```json
{
    "customers": [
        "23101442",
        "23101441",
        "23101440",
        "23101439",
        "23101438"
    ],
    "template": "Maaf toko {%shopname%} libur,\nuntuk semua chat akan dibalas saat toko kembali aktif. "
}
```

> Example response:

```json
{
    "response": "Success",
    "message": "5 Message sent successfully",
    "data": {
        "text": "Maaf toko *PT Ayo Technoidea* libur,  \nuntuk semua chat akan dibalas saat toko kembali aktif.",
        "msid": "",
        "status": 1
    }
}
```
Send message to multiple customers.

### Endpoint
`POST https://api.ngorder.id/api/open/woowa/customer/messages`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
customers | []integer | Customers ID taken from [Get Customers](/#get-customers)
template | string | Message template text






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
token | string | Bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID taken from [Get Orders](/#get-orders)
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
token | string | Bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Order ID taken from [Get Orders](/#get-orders)
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
token | string | Bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
order_id | integer | Order ID taken from [Get Orders](/#get-orders)

## template
> Example request:

```json
```

> Example response:

```json
```
m

### Endpoint
`GET https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
token | string | Bearer token

### Query
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
curl "https://example.com/api/kittens" \
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

`GET https://example.com/api/kittens`

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
curl "https://example.com/api/kittens/2" \
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

`GET https://example.com/kittens/<ID>`

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
curl "https://example.com/api/kittens/2" \
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

`DELETE https://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->
