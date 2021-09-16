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
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword | string | Product name to look for. Min: 3. Max: 50
type | string | Promo type. Available values: `PRODUCT` or `EXPEDITION`
id `(optional)` | string | Promo ID taken from [Get Promos](#get-promos). Fill this if you want to check a certain promo
start_date `(optional)` | string | Start date range to search for promo. Format `yyyy-mm-dd`
end_date `(optional)` | string | End date range to search for promo. Format `yyyy-mm-dd`
couriers `(optional)` | integer | Couriers ID taken from [Get Expeditions](#get-expeditions)
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
Authorization | string | User's bearer token

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
customer_categories | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](#get-categories-2)
all_products | boolean | Promo applies to all product
selected_items | array | Selected items detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>products `optional`</td><td>`[]integer` List of products ID taken from [Get Products](#get-products). Required if`all_products: false` and `type: PRODUCT`</td></tr><tr><td>platforms</td><td>`[]string` List of platforms. Available values:`ORDER_APP`, `PROMO`, `PRIVOR`, `STOREFRONT` or `QUICK_ORDER`</td></tr><tr><td>couriers</td><td>`[]string` List of couriers ID taken from [Get Expeditions](#get-expeditions)</td></tr></table>







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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Promo ID taken from [Get Promos](#get-promos)








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
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Promo ID taken from [Get Promos](#get-promos)
group | string | Promo group. Available values: `PROMO` or `COUPON`.
type | string | Promo type. Available values: `PRODUCT` or `EXPEDITION`
name | string | Promo name
coupon_code `(optional)` | string | Coupon code. Required if `group: COUPON`
start_date | string | Promo start date. Format `yyyy-mm-dd hh:mm`. Cannot be less than the current date
end_date | string | Promo end date. Format `yyyy-mm-dd hh:mm`.
limits | array | Limits detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>usage_per_customer `(optional)`</td><td> `string` Usage per customer limit. Available values: `1 to 9` or leave empty for unlimited usage</td></tr><tr><td>promo_limit `(optional)`</td><td>`string` Total promo quota. Leave empty if unlimited</td></tr><tr><td>minimum_product `(optional)`</td><td>`integer` Minimum purchase of products before this promo applies</td></tr><tr><td>minimum_transaction `optional`</td><td>`integer` Minimum cost before this promo applies</td></tr></table>
is_active | boolean | Promo activation status
customer_categories | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](#get-categories-2)
all_products | boolean | Promo applies to all product
selected_items | array | Selected items detail <table><tr><th>Key</th><th>Value</th></tr><tr><td>products `optional`</td><td>`[]integer` List of products ID taken from [Get Products](#get-products). Required if`all_products: false` and `type: PRODUCT`</td></tr><tr><td>platforms</td><td>`[]string` List of platforms. Available values:`ORDER_APP`, `PROMO`, `PRIVOR`, `STOREFRONT` or `QUICK_ORDER`</td></tr><tr><td>couriers</td><td>`[]string` List of couriers ID taken from [Get Expeditions](#get-expeditions)</td></tr></table>





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
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
Promo ID taken from [Get Promos](#get-promos)