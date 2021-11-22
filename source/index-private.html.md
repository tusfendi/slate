---
title: Ngorder API - Documentation

language_tabs: # must be one of https://git.io/vQNgJ
  - JSON

toc_footers:

includes:
  - user
  - shop
  - supplier
  - warehouse
  - product/product_category
  - product/product
  - stock_opname
  - stock_transfer
  - customer/customer_category
  - region
  - customer/customer
  - bank
  - expedition
  - marketplace
  - order/order_source
  - order/order_cost
  - order/order
  - order/cancel_order
  - storefront_privor
  - setting_storefront_courier
  - shipment
  - setting_payment_fee
  - payment
  - expense
  - report
  - analyzer
  - notification
  - billing
  - woowa/customer
  - woowa/order
  - errors

search: true

code_clipboard: true
---

# Introduction

Ngorder provides API that can be used to integrate your system with our platform. The API is built based on REST concept and will return JSON formatted data upon your requests. In order to use our API, you must have an existing active shop in our application.

## Types of Parameter Location
> Example of body parameter:

```json
{
  "param_1": 1,
  "param_2": 2
}
```

### Body

A JSON that sent with the request, usually used in POST or PATCH requests.

### Path
Located inside the URL used to identify a resource uniquely, usually used in GET requests. example:

`https://api.ngorder.id/api/open/resource/{id}`

### Query
Located inside the URL that appear after question mark, it's usually optional and used in GET requests. example:

`https://api.ngorder.id/api/open/resource?{key=value}`

<!-- Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/slatedocs/slate). Feel free to edit it and use it as a base for your own API's documentation. -->

# Authentication

In order to use our API, you can securely authorize your application using either Key Authentication or OAuth 2, this key will be available if you are using our [**Platinum package**](https://app.ngorder.id/upgrade?app=platinum-12), if you're already using our Platinum package be sure to check your key as it's updated every year. Both authorization method provide access to the same API, only the endpoints are slightly different.

<!-- > To authorize, use this code: -->

<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
``` -->

<!-- > Make sure to replace `meowmeowmeow` with your API key. -->


<!-- <aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside> -->









































































































































<!-- ## template
> Example request:

```json
```

> Example response:

```json
```
m

### Endpoint
`GET https://api.ngorder.id/api/open/`

### Header
Parameter | Type | Description
--------- | ---- | -----------
Authorization | string | User's bearer token

### Query
Parameter | Type | Description
--------- | ---- | ----------- -->
<!-- ## Get All Kittens

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

```shell
curl "https://example.com/api/kittens" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "https://example.com/api/kittens/2" \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET https://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "https://example.com/api/kittens/2" \
  -X DELETE \
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE https://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete
 -->
