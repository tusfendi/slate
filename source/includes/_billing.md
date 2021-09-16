# Billing
## Get Active Addons
> Example request:

```json
```

> Example response:

```json
{
  "data": [
    {
      "sort": 1,
      "class": "app",
      "button_title": "Upgrade",
      "message": null,
      "sub_message": "Expired Pada Rabu, 26 Jan 2022",
      "active": true,
      "logo": "https://sgp1.digitaloceanspaces.com/icon/upgrade/app.png",
      "link": "https://app.ngorder.id/upgrade?app=platinum-12",
      "package": "App Platinum"
    },
    {
      "sort": 2,
      "class": "storefront",
      "button_title": "Perpanjang Sekarang",
      "message": null,
      "sub_message": "Layaran Expired",
      "active": true,
      "logo": "https://sgp1.digitaloceanspaces.com/icon/upgrade/storefront.svg",
      "link": "https://app.ngorder.id/upgrade?storefront=sf-pro",
      "package": "Storefront Pro"
    },
    {
      "sort": 3,
      "class": "shopee",
      "button_title": "Upgrade",
      "message": null,
      "sub_message": "Expired Pada Selasa, 6 Feb 2024",
      "active": true,
      "logo": "https://sgp1.digitaloceanspaces.com/icon/upgrade/shopee.svg",
      "link": "https://app.ngorder.id/upgrade?shopee=shopee-unlimited",
      "package": "Shopee Unlimited 6"
    },
    {
      "sort": 4,
      "class": "sms",
      "button_title": "Upgrade",
      "message": "Credit: 1245",
      "sub_message": "Expired Pada Minggu, 2 Jan 2022",
      "active": true,
      "logo": "https://sgp1.digitaloceanspaces.com/icon/upgrade/awb-notification.svg",
      "link": "https://app.ngorder.id/upgrade?sms=sms-1000",
      "package": "Notifikasi Resi"
    },
    {
      "sort": 5,
      "class": "mutation",
      "button_title": "Tambah Credit",
      "message": "Credit: 108000",
      "sub_message": null,
      "active": true,
      "logo": "https://sgp1.digitaloceanspaces.com/icon/upgrade/mutation.svg",
      "link": "https://app.ngorder.id/mutasi/credit",
      "package": "Mutasi Bank"
    },
    {
      "sort": 6,
      "class": "woowa",
      "button_title": "Upgrade",
      "message": null,
      "sub_message": "Expired Pada Kamis, 3 Nov 2022",
      "active": true,
      "logo": "https://sgp1.digitaloceanspaces.com/icon/upgrade/woowa.svg",
      "link": "https://app.ngorder.id/upgrade?woowa=woowa-economic",
      "package": "Woowa Economic"
    }
  ]
}
```
Get user active addons.

### Endpoint
`GET https://api.ngorder.id/api/open/billing/addons`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token





## Get Billing List
> Example request:

```json
```

> Example response:

```json
{
  "start_date": "2018-10-18",
  "end_date": "2021-06-14",
  "data": [
    {
      "id": 15408,
      "invoice": "INV-00007-5-220",
      "invoice_url": "https://app.ngorder.id/xendit/606d14d439ade3401b332af5",
      "services": [
        "Shopee Basic - 3 bulan"
      ],
      "created_at": "2021-04-07T02:11:32.000000Z",
      "payment_date": "2021-04-07T02:11:32.000000Z",
      "xendit_id": "606d14d439ade3401b332af5",
      "status": "EXPIRED",
      "amount": 323500,
      "received_amount": 0,
      "payment_method": "Virtual Account",
      "bank_image": null
    },
    {
      "id": 15329,
      "invoice": "INV-00007-5-219",
      "invoice_url": "https://app.ngorder.id/xendit/6064433a0a5cca4019b9a020",
      "services": [
        "Ngorder Premium - 1 th"
      ],
      "created_at": "2021-03-31T09:39:06.000000Z",
      "payment_date": "2021-03-31T09:39:06.000000Z",
      "xendit_id": "6064433a0a5cca4019b9a020",
      "status": "EXPIRED",
      "amount": 682500,
      "received_amount": 0,
      "payment_method": "Virtual Account",
      "bank_image": null
    }
  ],
  "meta": {
    "pagination": {
      "total": 220,
      "count": 2,
      "per_page": 2,
      "current_page": 1,
      "total_pages": 110,
      "links": {
        "next": "https://api.ngorder.id//api/open/billing?pagination_offset=2"
      }
    }
  }
}
```
Get user billing histories.

### Endpoint
`GET https://api.ngorder.id/api/open/billing`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
start_date `(optional)` | string | Date from which data are requested. Format `yyyy-mm-dd`
end_date `(optional)` | string | Date to which data are requested. Format `yyyy-mm-dd`
per_page `(optional)` | integer | Data per page. Default `50`. Max `100`
pagination_offset `(optional)` | integer | Page number. Default `1`





## Download Invoice
> Example request:

```json
```
Download invoice as PDF

### Endpoint
`GET https://api.ngorder.id/api/open/billing/{id}/download`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Path
Parameter | Type | Description
--------- | ---- | -----------
id | integer | Invoice ID