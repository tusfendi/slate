# Notification
## Get Notifications
> Example request:

```json
```

> Example response:

```json
{
  "unread_count": 38,
  "data": [
    {
      "id": "09d93ba2-45ba-44ac-b1d7-0479346f1781",
      "title": "Orderan baru dari Storefront",
      "content": "<strong>Zonen</strong> memesan tas rampage UWU biru muda, sudah konfirmasi bayar <strong>Rp721.000</strong>, mohon segera konfirmasi pemesanan",
      "body": "Zonen memesan Tas Rampage biru muda, sudah konfirmasi bayar Rp721.000, mohon segera konfirmasi pemesanan",
      "icon": "https://sgp1.digitaloceanspaces.com/ngorder-1/icon/storefront.png",
      "web_path": "order/form_confirmation/1632919",
      "action": {
        "data_id": 1632919,
        "type": "confirm_order",
        "api_path": "/api/open/order/confirm"
      },
      "time_ago": "1 bulan yang lalu"
    },
    {
      "id": "caa3d67a-182e-4bb9-8495-c3d01da1acf9",
      "title": "Orderan baru dari Storefront",
      "content": "<strong>Naya Anindita</strong> memesan Kaos Polo L abu-abu, sudah konfirmasi bayar <strong>Rp57.280</strong>, mohon segera konfirmasi pemesanan",
      "body": "Naya Anindita memesan Kaos Polo L abu-abu, sudah konfirmasi bayar Rp57.280, mohon segera konfirmasi pemesanan",
      "icon": "https://sgp1.digitaloceanspaces.com/ngorder-1/icon/storefront.png",
      "web_path": "order/form_confirmation/1632818",
      "action": {
        "data_id": 1632818,
        "type": "confirm_order",
        "api_path": "/api/open/order/confirm"
      },
      "time_ago": "1 bulan yang lalu"
    }
  ],
  "meta": {
    "pagination": {
      "total": 42,
      "count": 2,
      "per_page": 20,
      "current_page": 3,
      "total_pages": 3,
      "links": {
        "previous": "https://api.ngorder.id/api/open/notification?pagination_offset=2"
      }
    }
  }
}
```
Get all notifications for selected type.

### Endpoint
`GET https://api.ngorder.id/api/open/notification`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
type `(optional)` | string | Notification type. Available values: `ACTIVITY` or `NEWS`. Default value: `ACTIVITY`
per_page `(optional)` | integer | Data per page. Default `20`
pagination_offset `(optional)` | integer | Page number. Default `1`





## Get Unread Count
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "activity": 390,
    "news": 43,
    "activity_display": "99+",
    "news_display": "43"
  }
}
```
Get unread notifications count.

### Endpoint
`GET https://api.ngorder.id/api/open/notification/unread`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token






## Push Device Token
> Example request:

```json
```

> Example response:

```json
{
  "data": {
    "token": "abcdefGHIJKL",
    "device": "Samsung S20+",
    "user_id": 51235
  }
}
```
Push device token.

### Endpoint
`POST https://api.ngorder.id/api/open/notification/token`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
Authorization | integer | Device Firebase cloud messaging token






## Read Notifications
> Example request:

```json
```

> Example response:

```json
{
  "request_id": "6059a5b058d79",
  "response": "Success"
}
```
Mark notification as read.

### Endpoint
`POST https://api.ngorder.id/api/open/notification/read`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
id `(optional)` | string | Notification ID taken from [Get Notifications](#get-notifications)
type `(optional)` | string | Notification type. Available values: `ACTIVITY` or `NEWS`. Default value: `ACTIVITY`