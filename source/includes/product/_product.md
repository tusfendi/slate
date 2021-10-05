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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Product name or product variation SKU to look for
shop_id `(optional)` | integer | Shop ID
category `(optional)` | string | Product category. Available values: `UNCATEGORIZED`, `ARCHIVED` or the ID of [Product Category](#product-category) that has been created
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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
        "id_order": null,
        "stock_opname_id": 99,
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
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Product variant ID
warehouse_id `(optional)` | integer | Variant warehouse ID taken from [Get Warehouse](#get-warehouses)
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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
wholesale `(optional)` | [][Wholesale](#update-product-wholesale-data) | Wholesale data
is_warehouse `(optional)` | integer | Product warehouse status. Available value: `1` or `0`. Default: `0`
publish_status | string | Product publish status. Available values: `Y` or `N`
show_stock | string | Show product stock in Storefront or Privor status. Available value: `Y` or `N`
has_variation | string | Product variation status. Available value: `Y` or `N`
variations `(optional)` | [][Variations](#update-product-variations-data) | Product variations details

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
category `(optional)` | string | Product category. Available values: `UNCATEGORIZED`, `ARCHIVED` or the ID of [Product Category](#product-category) that has been created
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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | []integer | Product ID