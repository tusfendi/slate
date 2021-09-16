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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Product category ID