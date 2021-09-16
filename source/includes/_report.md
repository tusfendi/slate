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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | integer | Filter the data. Available values: `BY_DATE` or `BY_MONTH`. Default value: `BY_DATE`
month `(optional)` | integer | Month number. Format `m` (without leading zero). Required if `type: BY_MONTH`
year `(optional)` | integer | Year number. Format `yy` (last two digits). Required if `type: BY_MONTH`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
