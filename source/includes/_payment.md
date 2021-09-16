# Payment
## Get Payment List
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "id": 1457,
      "transaction_number": "#INV1457",
      "type": {
        "id": "1",
        "status": "+"
      },
      "date": "2021-03-24 13:32:24",
      "title": "Pembayaran Order",
      "description": "Pembayaran order #12027 menggunakan Saldo Orderpay dari canceled order",
      "nominal": 167000
    },
    {
      "id": 1418,
      "transaction_number": "#INV1418",
      "type": {
        "id": "1",
        "status": "+"
      },
      "date": "2021-03-15 14:27:46",
      "title": "Pembayaran Order",
      "description": "Pembayaran order #12028 menggunakan Saldo Orderpay dari canceled order",
      "nominal": 167000
    }
  ],
  "meta": {
    "pagination": {
      "total": 15,
      "count": 2,
      "per_page": 2,
      "current_page": 1,
      "total_pages": 8,
      "links": {
        "next": "https://api.ngorder.id/api/open/payment?start_date=2021-01-31&end_date=2021-04-01&per_page=2&pagination_offset=2"
      }
    }
  }
}
```
Get list of payments.

### Endpoint
`GET https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
payment_type `(optional)` | string | Payment type. Available values: `ORDER_PAY` or `PAYMENT_GATEWAY`. Default value: `ORDER_PAY`
funds `(optional)` | string | Fund status. Available values: `OUTGOING` or `INCOMING`
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`. Default value: start date of current month.
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`. Default value: today
per_page `(optional)` | integer | Data per page. Default value: `10`
pagination_offset `(optional)` | integer | Page number. Default value: `1`







## Get OrderPay Balance
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "total": 13484522,
    "withdrawal_allowed": 7813017,
    "onhold_total": 5671505,
    "balance_onhold": 4928504,
    "withdrawal_onhold": 743001
  }
}
```
Get OrderPay balance on your account.

### Endpoint
`GET https://api.ngorder.id/api/open/payment/orderpay-balance`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token










## Get Xendit Balance
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "balance": 13484522
  }
}
```
Get Xendit balance on your account.

### Endpoint
`GET https://api.ngorder.id/api/open/payment/xendit/balance`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token





## Withdraw
> Example request:

```json
```

> Example response:

```json
{
  "response": "Success",
  "message": "Withdrawal request is successful, we will process it soon"
}
```
Withdrawal.

### Endpoint
`POST https://api.ngorder.id/api/open/payment/withdraw`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
xendit_bank_id | integer | Bank ID taken from [Xendit Master Data](#get-xendit-master-data)
nominal | integer | Withdrawal amount. Min Rp50.000. The admin fee of Rp45.000 will be automatically added to the final nominal.
holder_name | string | Holder name
account_number | integer | Account number