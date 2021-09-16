# Marketplace
## Get Marketplaces
> Example request:

```json

```
> Example response:

```json
{
  "data": [
    {
      "marketplace_id": 1,
      "marketplace_name": "Tokopedia"
    },
    {
      "marketplace_id": 2,
      "marketplace_name": "Bukalapak"
    },
    {
      "marketplace_id": 3,
      "marketplace_name": "Shopee"
    },
    {
      "marketplace_id": 4,
      "marketplace_name": "Instagram"
    },
    {
      "marketplace_id": 5,
      "marketplace_name": "Whatsapp"
    },
    {
      "marketplace_id": 6,
      "marketplace_name": "Lazada"
    },
    {
      "marketplace_id": 7,
      "marketplace_name": "Facebook"
    },
    {
      "marketplace_id": 8,
      "marketplace_name": "Website Lain"
    }
  ]
}
```
Get marketplaces.

### Endpoint
`GET https://api.ngorder.id/api/open/marketplace`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token