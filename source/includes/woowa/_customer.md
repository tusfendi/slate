# Woowa Customer
## Get Template
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "id": 23,
      "type": "CUSTOM_NOTIFICATION",
      "template": "Maaf toko {%shopname%} libur,\nuntuk semua chat akan dibalas saat toko kembali aktif. "
    },
    {
      "id": 27,
      "type": "PROMO",
      "template": "Halo kak {%buyer%}, sedang ada promo 35% untuk semua product dan varian"
    }
  ]
}
```
Get message templates.

### Endpoint
`GET https://api.ngorder.id/api/open/woowa/customer`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token




## Send Bulk Message
> Example request:

```json
{
    "customers": [
        "23101442",
        "23101441",
        "23101440",
        "23101439",
        "23101438"
    ],
    "template": "Maaf toko {%shopname%} libur,\nuntuk semua chat akan dibalas saat toko kembali aktif. "
}
```

> Example response:

```json
{
    "response": "Success",
    "message": "5 Message sent successfully",
    "data": {
        "text": "Maaf toko *PT Ayo Technoidea* libur,  \nuntuk semua chat akan dibalas saat toko kembali aktif.",
        "msid": "",
        "status": 1
    }
}
```
Send message to multiple customers.

### Endpoint
`POST https://api.ngorder.id/api/open/woowa/customer`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Body
Parameter | Type | Description
--------- | ---- | -----------
customers | []integer | Customers ID taken from [Get Customers](#get-customers)
template | string | Message template text