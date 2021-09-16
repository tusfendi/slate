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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Customer category ID
code | string | Customer category code
category_name `(optional)` | string | Category name
status `(optional)` | string | Active status. Available values: `Y` (active) or `N` (non active)
discount_access `(optional)` | string | Discount access for this category
wholesale_access `(optional)` | string | Wholesale access for this category