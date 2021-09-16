# Region
## Get Regions
> Example response:

```json
{
  "data": [
    {
      "_id": "5d1d86101449f91d8b32cdce",
      "id": 3627,
      "subdistrict": "Tajinan",
      "district": {
        "id": 255,
        "name": "Kabupaten Malang"
      },
      "province": {
        "id": 11,
        "name": "Jawa Timur"
      },
      "fullname": "Tajinan, Kabupaten Malang, Jawa Timur",
      "postal_code": [
        "65172"
      ]
    }
  ],
  "meta": {
    "pagination": {
      "total": 1,
      "count": 1,
      "per_page": 10,
      "current_page": 1,
      "total_pages": 1,
      "links": {}
    }
  }
}
```
Get region data that will be used when [creating a new customer](#create-customer)

### Endpoint
`GET https://api.ngorder.id/api/open/region`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | -----------
keyword `(optional)` | string | District name to look for
per_page `(optional)` | integer | Data per page. Default `1`
pagination_offset | integer | Page number. Default `1`