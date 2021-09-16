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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Expense ID taken from [Get Expenses](#get-expenses)
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
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Expense ID taken from [Get Expenses](#get-expenses)