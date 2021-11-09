# Stock Opname
Stock opname is a feature used to adjust stock in the system and real stock in the warehouse.

## Create Stock Opname
> Example request:

```json
{
    "warehouse_id": 0,
    "description": "Stok opname bulanan",
    "stock_adjustment": [
        {
            "variation_id": 10113507,
            "warehouse_stock": 35
        },
        {
            "variation_id":10113503,
            "warehouse_stock":35
        }
    ]
}
```

> Example success response:

```json
{
    "response": "Success",
    "data": {
        "id": 55,
        "description": "Stok opname Gudang bulanan",
        "variation_total": 2,
        "progress_status": "ON PROGRESS",
        "warehouse": {
            "id": 0,
            "name": "Gudang Utama"
        }
    }
}
```

The process of creating stock opname will automatically run in the background if there are a lot of customized product stocks. The progress status of the stock taking can be seen in the `progress_status` response. the `progress_status` can contain `ON PROGRESS` / `SUCCESS`.

### Endpoint
`POST https://api.ngorder.id/api/open/stock-opname`
### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
warehouse_id | integer | Warehouse ID taken from [warehouse](#warehouse)
description | string | Stock Opname Description
stock_adjustment | array | 
stock_adjustment[][variation_id] | integer | variation id from frome [search variation for stock opname](#search-variation-for-stock-opname)
stock_adjustment[][warehouse_stock] | integer | actual stock in warehouse

## Import Stock Opname

Import stock opname is another way to do stock opname by uploading excel file. You are only allowed to change the warehouse stock from the excel file you downloaded. Note: please upload the excel file according to the specified format from [generate stock opname template](#generate-template-stock-opname). Import process will run in the background and maximum file you can upload is 2 Megabytes.

> Example success response:

```json
{
    "response": "Success",
    "message": "Import is in progress"
}
```
### Endpoint
`POST https://api.ngorder.id/api/open/stock-opname/import`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
file | file | file from [generate stock opname template](#generate-template-stock-opname) (xlsx format)

## Generate Template Stock Opname

This API generates files in .xlsx format. This file contains warehouse information and product data variants that already exist in the selected warehouse. Note: You can only adjust warehouse stock. You are not allowed to change the existing product sku data and warehouse code in the file.

If you have customized warehouse stock, you can upload this file in [Import Stock Opname](#import-stock-opname)

### Endpoint
`GET https://api.ngorder.id/api/open/stock-opname/import`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
warehouse_id | integer | Warehouse ID taken from [warehouse](#get-warehouses), required

## Get Stock Opname List

> Example success response:

```json
{
    "data": [
        {
            "id": 55,
            "description": "Stok opname Gudang perdana",
            "variation_total": 3,
            "progress_status": "ON PROGRESS",
            "warehouse": {
                "id": 5,
                "name": "Tito Malang"
            },
            "created_at": "2021-10-04 10:29:23"
        },
        {
            "id": 54,
            "description": "Stok opname Gudang dengan rabbit",
            "variation_total": 2,
            "progress_status": "ON PROGRESS",
            "warehouse": {
                "id": 0,
                "name": "Gudang Utama"
            },
            "created_at": "2021-10-04 10:29:21"
        }
    ],
    "meta": {
        "pagination": {
            "total": 55,
            "count": 2,
            "per_page": 2,
            "current_page": 1,
            "total_pages": 28,
            "links": {
                "next": "https://api.ngorder.id/api/open/stock-opname?per_page=2&pagination_offset=2"
            }
        }
    }
}

```

### Endpoint
`GET https://api.ngorder.id/api/open/stock-opname`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
per_page `(optional)` | integer | Data per page. Default value: `20`
pagination_offset `(optional)` | integer | Page number. Default value: `1`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`. Default value:30 days ago
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
warehouse_id `(optional)` | integer | Warehouse ID taken from [warehouse](#get-warehouses), default is show all data
user_id `(optional)` | integer | User ID who made the stock opname

## Get Stock Opname Detail
> Example success response:

```json
{
    "data": {
        "id": 53,
        "description": "Stok opname Gudang Malang",
        "progress_status": "SUCCESS",
        "variation_total": 3,
        "processed": 3,
        "warehouse": {
            "id": 5,
            "name": "Tito Malang"
        },
        "created_by": {
            "id": "5",
            "email": "tusfendi@gmail.com",
            "name": "tusfendi"
        },
        "created_at": "2021-10-01T01:42:24.000000Z"
    }
}
```

Get stock opname detail data.

### Endpoint
`GET https://api.ngorder.id/api/open/stock-opname/{id}/detail`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Stock Opname ID


## Get Transaction Stock Opname Detail
> Example success response:

```json
{
    "data": [
        {
            "id": 60,
            "variation_id": 8055498,
            "full_name": "Kaos Polos XL",
            "thumbnail_url": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
            "sku": "PBV-LL2",
            "stock_adjustment": {
                "warehouse_stock": 35,
                "system_stock": 10,
                "changed_stock": 25
            }
        },
        {
            "id": 61,
            "variation_id": 8055497,
            "full_name": "Kaos Polos L",
            "thumbnail_url": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
            "sku": "PBV-LL0",
            "stock_adjustment": {
                "warehouse_stock": 35,
                "system_stock": 35,
                "changed_stock": 0
            }
        },
        {
            "id": 62,
            "variation_id": 8055499,
            "full_name": "Kaos Polos M",
            "thumbnail_url": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
            "sku": "PBV-LL6",
            "stock_adjustment": {
                "warehouse_stock": 35,
                "system_stock": 35,
                "changed_stock": 0
            }
        }
    ],
    "meta": {
        "pagination": {
            "total": 3,
            "count": 3,
            "per_page": 50,
            "current_page": 1,
            "total_pages": 1,
            "links": []
        }
    }
}
```

Get stock opname transaction.

### Endpoint
`GET https://api.ngorder.id/api/open/stock-opname/transaction`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Stock Opname ID
per_page `(optional)` | integer | Data per page. Default value: `50`
pagination_offset `(optional)` | integer | Page number. Default value: `1`


## Search Variation For Stock Opname

> Example request:

```json
{
    "keyword" : "kaos Leo polos",
    "warehouse_id" : 5
}
```

> Example success response:

```json
{
    "warehouse_id": 5,
    "data": [
        {
            "variation_id": 10204994,
            "name": "Kaos Leo Polos L Hijau",
            "sku": "KLP-HIJ-L-L6Q",
            "thumbnail_url": "https://cepat.b-cdn.net/7/products/kaos-leo-polos-warna-warni-1633061215514.jpeg",
            "system_stock": 10
        },
        {
            "variation_id": 10204993,
            "name": "Kaos Leo Polos L Merah",
            "sku": "KLP-MER-L-L6E",
            "thumbnail_url": "https://cepat.b-cdn.net/7/products/kaos-leo-polos-warna-warni-1633061178898.jpg",
            "system_stock": 0
        }
    ]
}
```

Search variation for create stock opname

### Endpoint
`GET https://api.ngorder.id/api/open/stock-opname/variation`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
product_id `(optional)` | integer | Product ID. must without warehouse_id and keyword
keyword `(optional)` | integer | required with keyword, must without product_id. value from product name / SKU
warehouse_id | integer | required, from [warehouse](#warehouse)
