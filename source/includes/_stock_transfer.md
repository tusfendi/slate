# Stock Transfer
Stock transfer is a feature to move stock between warehouses, this feature can be accessed if you have more than one warehouse.

## Create Stock Transfer
> Example request:

```json
{
    "origin_warehouse_id": 4,
    "destination_warehouse_id":5,
    "description": "Stok transfer Gudang Surabaya ke gudang Malang",
    "stock_adjustment": [
        {
            "variation_id": 8055499,
            "transfer_stock": 300
        },
        {
            "variation_id": 8055495,
            "transfer_stock": 3
        },
        {
            "variation_id": 8055496,
            "transfer_stock": 6
        }
    ]
}
```

> Example success response:

```json
{
    "response": "Sukses",
    "data": {
        "id": 30,
        "description": "Stok transfer Gudang Surabaya ke gudang Malang",
        "origin_warehouse": {
            "id": 4,
            "name": "Gudang Yai"
        },
        "destination_warehouse": {
            "id": 5,
            "name": "Tito Malang"
        },
        "created_at": "2021-11-19 11:07:50"
    }
}
```

Maximum variation in one time making stock transfer is 100

### Endpoint
`POST https://api.ngorder.id/api/open/stock-transfer`
### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
origin_warehouse_id | integer | Origin Warehouse ID taken from [warehouse](#warehouse)
destination_warehouse_id | integer | Destination Warehouse ID taken from [warehouse](#warehouse)
description | string | Stock Transfer Description
stock_adjustment | array | 
stock_adjustment[][variation_id] | integer | variation id from frome [search variation for stock transfer](#search-variation-for-stock-transfer)
stock_adjustment[][transfer_stock] | integer | transfer stock total


## Get Stock Transfer List

> Example success response:

```json
{
    "data": [
        {
            "id": 30,
            "description": "Stok transfer Gudang Surabaya ke gudang Malang",
            "origin_warehouse": {
                "id": 4,
                "name": "Gudang Surabaya"
            },
            "destination_warehouse": {
                "id": 5,
                "name": "gudang Malang"
            },
            "created_at": "2021-11-19 11:07:50"
        },
        {
            "id": 29,
            "description": "Stok transfer Gudang Utama ke gudang Malang",
            "origin_warehouse": {
                "id": 0,
                "name": "Gudang Utama"
            },
            "destination_warehouse": {
                "id": 5,
                "name": "gudang Malang"
            },
            "created_at": "2021-11-17 14:51:11"
        }
    ],
    "meta": {
        "pagination": {
            "total": 30,
            "count": 2,
            "per_page": 2,
            "current_page": 1,
            "total_pages": 15,
            "links": {
                "next": "https://api.ngorder.id/api/open/stock-transfer?per_page=2&pagination_offset=2"
            }
        }
    }
}

```

### Endpoint
`GET https://api.ngorder.id/api/open/stock-transfer`

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
origin_warehouse_id `(optional)` | integer | Origin Warehouse ID taken from [warehouse](#get-warehouses), default is show all data
destination_warehouse_id `(optional)` | integer | Destination Warehouse ID taken from [warehouse](#get-warehouses), default is show all data
user_id `(optional)` | integer | User ID who made the stock Transfer

## Get Stock Transfer Detail
> Example success response:

```json
{
    "data": {
        "id": 53,
        "description": "Stok Transfer Gudang Malang",
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

Get stock Transfer detail data.

### Endpoint
`GET https://api.ngorder.id/api/open/stock-transfer/{id}/detail`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Stock Transfer ID


## Get Transaction Stock Transfer Detail
> Example success response:

```json
{
    "data": [
        {
            "id": 40,
            "variation_id": 8055499,
            "product_name": "Baju Takwa Batik",
            "variant_name": "X merah",
            "thumbnail_url": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
            "sku": "PBV-LL6",
            "transfered_stock": 3
        },
        {
            "id": 41,
            "variation_id": 8055495,
            "product_name": "Baju Takwa Polos",
            "variant_name": "-",
            "thumbnail_url": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
            "sku": "PBV-LKC00",
            "transfered_stock": 3
        },
        {
            "id": 42,
            "variation_id": 8055496,
            "product_name": "Baju Takwa 3 per 4",
            "variant_name": "-",
            "thumbnail_url": "https://s3-ap-southeast-1.amazonaws.com/technoidea/products/default.jpg",
            "sku": "PBV-S-LLE",
            "transfered_stock": 6
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

Get stock Transfer transaction.

### Endpoint
`GET https://api.ngorder.id/api/open/stock-transfer/transaction`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Stock Transfer ID
per_page `(optional)` | integer | Data per page. Default value: `50`
pagination_offset `(optional)` | integer | Page number. Default value: `1`


## Search Variation For Stock Transfer

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
            "product_name": "Kaos Leo Polos",
            "variation_name": "L Hijau",
            "sku": "KLP-HIJ-L-L6Q",
            "thumbnail_url": "https://cepat.b-cdn.net/7/products/kaos-leo-polos-warna-warni-1633061215514.jpeg",
            "system_stock": 10
        },
        {
            "variation_id": 10204993,
            "name": "Kaos Leo Polos L Merah",
            "product_name": "Kaos Leo Polos",
            "variation_name": "L Merah",
            "sku": "KLP-MER-L-L6E",
            "thumbnail_url": "https://cepat.b-cdn.net/7/products/kaos-leo-polos-warna-warni-1633061178898.jpg",
            "system_stock": 0
        }
    ]
}
```

Search variation for create stock Transfer.

### Endpoint
`GET https://api.ngorder.id/api/open/stock-transfer/variation`

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
