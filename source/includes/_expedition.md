# Expedition
## Get Expeditions
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "rate_name": "REG",
      "logistic_name": "JNE",
      "show_name": "Regular",
      "pickup_available": "AVAILABLE"
    },
    {
      "id": 2,
      "rate_name": "YES",
      "logistic_name": "JNE",
      "show_name": "Express",
      "pickup_available": "AVAILABLE"
    },
    {
      "id": 3,
      "rate_name": "OKE",
      "logistic_name": "JNE",
      "show_name": "Regular",
      "pickup_available": "AVAILABLE"
    },
    {
      "id": 4,
      "rate_name": "CTC",
      "logistic_name": "JNE",
      "show_name": "Regular",
      "pickup_available": "AVAILABLE"
    }
  ]
}
```
Get all expeditions data

### Endpoint
`GET https://api.ngorder.id/api/open/expedition`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

## Get Active List
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "id": 1,
      "rate_name": "REG",
      "logistic_name": "JNE",
      "show_name": "Regular",
      "logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/jne.png",
      "pickup_available": "AVAILABLE"
    },
    {
      "id": 44,
      "rate_name": "REGPACK",
      "logistic_name": "Lion Parcel",
      "show_name": "Regular",
      "logo_url": "https://ngorder-1.sgp1.digitaloceanspaces.com/courier/lionparcel.png",
      "pickup_available": "AVAILABLE"
    }
  ],
  "meta": {
    "pagination": {
      "total": 4,
      "count": 4,
      "per_page": 2,
      "current_page": 1,
      "total_pages": 2,
      "links": {
        "next": "https://api.ngorder.id/api/open/expedition/active?pagination_offset=2"
      }
    }
  }
}
```
Get expedition enabled for your shop. You can manage this by going <a href="https://app.ngorder.id/setting/courier" target="_blank">here</a> or on mobile app go to `Setting` > `Kurir` > `Kurir`.

### Endpoint
`GET https://api.ngorder.id/api/open/expedition/active`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | Courier name to look for. Max `20`
per_page `(optional)` | integer | Data per page. Default `10`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default `1`


## Get Cost
> Example request:

```json

```
> Example response:

```json
{
  "status": {
    "code": 1,
    "message": "Success"
  },
  "data": {
    "regular": [
      {
        "name": "SAP",
        "logo_url": "https://cdn.shipper.cloud/logistic/small/SAP.png",
        "rate_id": 349,
        "show_id": 1,
        "rate_name": "Reguler",
        "stop_origin": 3870,
        "stop_destination": 5023,
        "weight": 1,
        "volumeWeight": 0.1667,
        "finalWeight": 1,
        "itemPrice": 120000,
        "item_price": 120000,
        "finalRate": 37500,
        "insuranceRate": 360,
        "compulsory_insurance": 0,
        "liability": 0,
        "discount": 0,
        "min_day": 3,
        "max_day": 3,
        "pickup_agent": 1,
        "is_pickup_available": 1
      }
    ],
    "express": [
      {
        "name": "SAP",
        "logo_url": "https://cdn.shipper.cloud/logistic/small/SAP.png",
        "rate_id": 350,
        "show_id": 2,
        "rate_name": "One Day Service",
        "stop_origin": 3870,
        "stop_destination": 5023,
        "weight": 1,
        "volumeWeight": 0.1667,
        "finalWeight": 1,
        "itemPrice": 120000,
        "item_price": 120000,
        "finalRate": 16000,
        "insuranceRate": 360,
        "compulsory_insurance": 0,
        "liability": 0,
        "discount": 0,
        "min_day": 1,
        "max_day": 1,
        "pickup_agent": 1,
        "is_pickup_available": 1
      }
    ],
    "trucking": []
  },
  "meta": {
    "origin": {
      "area_id": "334",
      "district_id": "334",
      "desc": "Padangbai, Manggis, Karangasem"
    },
    "destination": {
      "area_id": "11677",
      "district_id": "334",
      "desc": "Sukaresmi, Ranca Bali, Bandung, Kab."
    },
    "weight": {
      "total": "1",
      "type": "Kg"
    },
    "is_shipper_api": true,
    "use_cod": true
  }
}
```
Get expedition cost.

### Endpoint
`GET https://api.ngorder.id/api/open/expedition/cost`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
origin_id | integer | District ID taken from [Region](#region)
destination_id | numeric | District ID taken from [Region](#region)
weight | integer | Total product weight
price | integer | Total price without shipping cost
is_privor `(optional)` | boolean | Privor status. Default `false`
is_shipper `(optional)` | boolean | Shipper status. Default `false`

## Tracking
> Example request:

```json

```
> Example response:

```json
{
  "0": 200,
  "response": "success",
  "data": {
    "awb_number": "00046512912705",
    "rate_name": "REG",
    "delivery_date": "2021-01-02 18:55",
    "delivery_time": "2021-01-02 18:55",
    "weight": 1,
    "sender_name": "Keren Shop Id",
    "origin_city": "Bandung",
    "receiver_name": "Tusfendi",
    "receiver_address": "Gedebage, Bandung",
    "receiver_city": "Gedebage, Bandung",
    "status": "DELIVERED",
    "consignees_name": null,
    "date_received": null,
    "time_received": null,
    "history": [
      {
        "date": "2021-01-02 10:58:00",
        "desc": "PICKREQ",
        "location": "Terima permintaan pick up dari [Tokopedia]"
      },
      {
        "date": "2021-01-02 18:55:00",
        "desc": "IN",
        "location": "Paket telah di input (manifested) di Bandung [Bandung Sumberasih]"
      },
      {
        "date": "2021-01-02 21:29:00",
        "desc": "OUT",
        "location": "Paket keluar dari Bandung [Bandung Sumberasih]"
      },
      {
        "date": "2021-01-03 08:25:00",
        "desc": "IN",
        "location": "Paket telah di terima di Bandung [Bandung Rancasari]"
      },
      {
        "date": "2021-01-03 10:07:00",
        "desc": "ANT",
        "location": "Paket dibawa [SIGESIT - Suhendra]"
      },
      {
        "date": "2021-01-03 12:48:00",
        "desc": "DELIVERED",
        "location": "Paket diterima oleh [Kamil - (YBS) Yang Bersangkutan]"
      }
    ],
    "logistic_name": "sicepat"
  }
}
```
Track air waybill number

### Endpoint
`GET https://api.ngorder.id/api/open/expedition/tracking`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
awb_number | string | Air waybill number
expedition_id | integer | Expedition ID taken from [Get Expeditions](#get-expeditions)
order_id | integer | Order ID