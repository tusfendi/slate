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
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | integer | Filter the data. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
category `(optional)` | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](#get-categories-2)
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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `optional` | string | Filter the data by type. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`



## Best Sales Channels
> Example request:

```json
```

> Example response:

```json
{
  "data": [
      {
          "title": "App Dashboard",
          "net_sales": 945000,
          "total": 7
      },
      {
          "title": "Private Order",
          "net_sales": 105000,
          "total": 1
      }
  ]
}
```
Get best sales channels.

### Endpoint
`GET https://api.ngorder.id/api/open/analyzer/sales-channel`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
per_page `(optional)` | integer | Data per page. Default value is without page limit
with_net_sales `(optional) | integer |  use this paramemter with value = `1` if you want to count net sales amount


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
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `optional` | string | Filter the data by type. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
category `(optional)` | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](#get-categories-2)
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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `optional` | string | Filter the data by type. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
category `(optional)` | string | Type of customer. Available values: `N` (Customer), `Y` (Reseller), `D` (Dropshipper) or custom category code taken from [customer categories](#get-categories-2)
order_by `(optional)` | string | Order the data. Available values: `TRANSACTION`, `SOLD_ITEMS`, `GROSS_SALES`, `NET_SALES` or `GROSS_PROFIT`. Just for owner's account. Default value: `TRANSACTION`