# Warehouse
You can take advantage of this API if you have product stock in several different warehouses. warehouse is optional, you can skip this API if you have 1 warehouse, because the system will initialize it as "Main Warehouse (**Gudang Utama**)"
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
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
warehouse | string | Warehouse name
supplier_id | integer | Supplier ID taken from [supplier](#supplier)
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
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
with_main_warehouse `(optional)` | boolean | Includes main warehouse. Default `false`
admin_permission `(optional)` | boolean | Only shows the warehouse according to each user's access. Default `false`, show permited access warehouse per user only
is_active `(optional)` | string | Warehouse active, in ALL,ACTIVE,NON_ACTIVE, default `ALL` if admin_permission empty and default `ACTIVE` if admin_permission `true` / `1`

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
Authorization | string | User's bearer token

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
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Warehouse ID
warehouse | string | Warehouse name
supplier_id | integer | Supplier ID taken from [supplier](#supplier)
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
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Warehouse ID