# Bank
## Get Master Data
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "bank_type": "bca",
      "bank_label": "Bank BCA",
      "bank_family": "bca",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bca.svg",
      "web_login_url": "https://www.klikbca.com",
      "status": 1
    },
    {
      "bank_type": "bcaSyariah",
      "bank_label": "Bank BCA Syariah",
      "bank_family": "bca",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bca.svg",
      "web_login_url": "https://ibank.klikbcasyariah.com",
      "status": 1
    },
    {
      "bank_type": "bni",
      "bank_label": "Bank BNI",
      "bank_family": "bni",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bni.svg",
      "web_login_url": "https://ibank.bni.co.id",
      "status": 1
    },
    {
      "bank_type": "bniBisnis",
      "bank_label": "Bank BNI Bisnis",
      "bank_family": "bni",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bni.svg",
      "web_login_url": "https://bnidirect.bni.co.id",
      "status": 1
    },
    {
      "bank_type": "bniBisnisSyariah",
      "bank_label": "Bank BNI Bisnis Syariah",
      "bank_family": "bni",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bni.svg",
      "web_login_url": "https://ibank.bni.co.id",
      "status": 1
    }
  ]
}
```
Get our main bank data.

### Endpoint
`GET https://api.ngorder.id/api/open/bank/master`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
without_business_bank `(optional)` | boolean | Exclude business bank. Default `false`

## Get Xendit Master Data
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "name": "Bank Sinarmas",
      "code": "SINARMAS",
      "can_disburse": 0,
      "can_name_validate": 0
    },
    {
      "id": 2,
      "name": "Bank Syariah Mandiri",
      "code": "MANDIRI_SYR",
      "can_disburse": 0,
      "can_name_validate": 0
    }
  ]
}
```
Get Xendit listed bank data

### Endpoint
` https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Bank name to look for


## Create Bank Account
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "bank_id": 26516,
    "name": "bca"
  }
}
```
Create bank account used in your shop.

### Endpoint
`POST https://api.ngorder.id/api/open/bank/create`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
bank_type | string | Bank type taken from [master data](#get-master-data)
account_number | numeric | Bank account number
holder_name | string | Bank account holder name
branch | string | Bank branch
username `(optional)` | string | Bank username
pin `(optional)` | string | Bank pin
corporate_id `(optional)` | string | Corporate ID. Required if `bank_type` is a business bank

## Get Shop Bank Accounts
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "bank_id": 1,
      "bank_name": "BCA",
      "bank_type": "bca",
      "branch": "Mulyorejo",
      "holder_name": "Budi",
      "account_number": "12345678",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bca.svg",
      "type": "BANK"
    },
    {
      "bank_id": 2,
      "bank_name": "BNIS",
      "bank_type": "bni",
      "branch": "Srono",
      "holder_name": "Budi",
      "account_number": "12345678",
      "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bnis.svg",
      "type": "BANK"
    }
  ]
}
```
Get bank data used in your shop.

### Endpoint
` https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type | string | Bank type. Available values: `BANK` or `PAYMENT GATEWAY`

## Get Bank Account Detail
> Example request:

```json

```
> Example response:

```json
{
  "bank_id": 1,
  "bank_name": "BCA",
  "bank_type": "bca",
  "branch": "Mulyorejo",
  "holder_name": "Budi",
  "account_number": "12345678",
  "image": "https://ngorder-1.sgp1.digitaloceanspaces.com/bank/bca.svg",
  "type": "BANK"
}
```
Get detail of bank account used in your shop.

### Endpoint
`GET https://api.ngorder.id/api/open/bank/{id}/detail`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | numeric | Bank ID

## Update Bank Account
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "bank_id": 123,
    "name": "bca"
  }
}
```
Update bank account used in your shop.

### Endpoint
`PATCH https://api.ngorder.id/api/open/bank/update`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
bank_id | integer | Bank ID
bank_type | string | Bank type taken from [master data](#get-master-data)
account_number `(optional)` | numeric | Bank account number
holder_name `(optional)` | string | Bank account holder name
branch `(optional)` | string | Bank branch
username `(optional)` | string | Bank username
pin `(optional)` | string | Bank pin
corporate_id `(optional)` | string | Corporate ID. Required if `bank_type` is a business bank

## Delete Mutation
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": {
    "bank_id": 100,
    "name": "mandiriBisnisMCM"
  }
}
```
Delete selected bank mutation.

### Endpoint
`DELETE https://api.ngorder.id/api/open/bank/delete-mutation/{bank_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
bank_id | integer | Bank ID

## Delete Bank
> Example request:

```json

```
> Example response:

```json
{
  "response": "Success",
  "data": null
}
```
Delete bank account used in your shop.

### Endpoint
`DELETE https://api.ngorder.id/api/open/bank/delete/{bank_id}`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
bank_id | integer | Bank ID