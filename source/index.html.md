---
title: HomeZada Partner API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby

toc_footers:
  - <a href='mailto:info@homezada.com'>Contact Us for a Partner API Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# HomeZada Partner API

Welcome to the HomeZada Partner Integration API documentation. You can use our API to access HomeZada API endpoints, which can get information on various Accounts and Properties in your partner store.

We have language bindings in Shell and Ruby. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

For questions about this API, or for help in setting up a new Partner account, please email us [here](mailto:info@homezada.com).

<aside class="success">
Remember — all data via this API is scoped by the Properties or Accounts only associated with your partner id. No other data is accessible.
</aside>

# JSON API

> A simple JSON API example call:

```shell
# Simple example of reading a Partner owned property
curl -i 
-H "Accept: application/vnntent-Type:application/vnd.api+json' 
--user your-partner-id:your-partner-api-secret 
https://secure.homezada.com/api/v1/properties/123456
```

```ruby

  require "net/http"
  require "uri"
  require "json"

  HOMEZADA_PARTNER_API_URL = "https://secure.homezada.com/api/v1/properties/123456"
  uri = URI.parse(HOMEZADA_PARTNER_API_URL)
  http = Net::HTTP.new(uri.host, uri.port)
  http.use_ssl = true if uri.scheme == 'https'
  request = Net::HTTP::Get.new(uri.request_uri)
  request.basic_auth(PARTNER_ID, PARTNER_API_SECRET)
  
  response = http.request(request)
  result = JSON.parse(response.body) if response.code == '200'
```

> The above command returns JSON structured like this:

```json
{
  "data": 
  { 
    "id": "123456",
    "type": "properties",
    "links":
    {
      "self": "https://secure.homezada.com/api/v1/properties/12356"
    },
    "attributes":
    {
      "name": "Our Forever Home",
      "description": "A really long description could go here with /n newlines.",
      "address1": "5567 Deerhorn Lane",
      "address2": "",
      "city": "North Vancouver",
      "state": "British Columbia",
      "zip": "V7R 4T3",
      "date-built": "1970-01-10",
      "number-of-bedrooms": "3",
      "number-of-bathrooms": "1.5",
      "square-feet": "3200 sq ft",
      "lot-size": "6000 sq ft",
      "properties-type": "SingleFamily",
      "parking-type": null,
      "cooling-system": null,
      "heating-system": null,
      "fireplace": null,
      "latitude-longitude": null,
      "county": null,
      "parcel-number": null,
      "census-tract-number": null,
      "country": "CA",
      "is-template": null,
      "pro-status": "BuySell Transfer",
      "customer-name": "Example Buyer",
      "customer-email": "example-buyerv@homezada.com",
      "customer-phone": null,
      "customer-mobile": null,
      "purchase-price": "6250002.0",
      "purchase-date": "1970-03-05",
      "appraisal-value": "515000.0",
      "appraisal-date": "1970-09-15",
      "property-tax-value": "496000.0",
      "property-tax-date": "2012-07-22",
      "sold-price": "695000.0",
      "sold-date": "1970-09-15",
      "buildings-insurance-value": "2000000.5",
      "buildings-insurance-renewal-date": "2014-06-25",
      "contents-insurance-value": "50000.0",
      "contents-insurance-renewal-date": "2014-06-25",
      "has-ground-pool": null,
      "status": "Previous",
      "property-tax-assessed-year": null,
      "currency": ""
    },
  "relationships":
  {
    "photos":
    {
      "links":
      {
        "self": "https://secure.homezada.com/api/v1/properties/1/relationships/photos",
        "related":"https://secure.homezada.com/api/v1/properties/1/relationships/photos"
      }
    }
  },
  "meta":
  {
    "copyright": "Copyright 2020 - HomeZada Inc.",
    "last_updated_at": "2019-10-22 22:03:00 UTC",
    "created_at": "2011-11-23 00:58:12 UTC"
  }
}
```

The HomeZada APIs are built around the concepts of the JSON API specification. The API supports creating, updating, deleting, and fetching resources and relationships via HTTPS verbs. More info on the JSON API specification can be found at [https://jsonapi.org/](https://jsonapi.org/).


# Authentication

> To authorize, use this code:

```shell
# Simple example of reading a Partner owned property
curl -i 
-H "Accept: application/vnntent-Type:application/vnd.api+json' 
--user PARTNER_ID:PARTNER_API_SECRET 
https://secure.homezada.com/api/v1/properties/123456
```

```ruby
  require "net/http"
  require "uri"
  require "json"

  HOMEZADA_PARTNER_API_URL = "https://secure.homezada.com/api/v1/properties/123456"
  uri = URI.parse(HOMEZADA_PARTNER_API_URL)
  http = Net::HTTP.new(uri.host, uri.port)
  http.use_ssl = true if uri.scheme == 'https'
  request = Net::HTTP::Get.new(uri.request_uri)
  request.basic_auth(PARTNER_ID, PARTNER_API_SECRET)
  
  response = http.request(request)
  result = JSON.parse(response.body) if response.code == '200'
```

> Make sure to replace `PARTNER_ID` with your API key and `PARTNER_API_SECRET` with your API secret.

In order to use the HomeZada Partner API, you must obtain a credentials pair (API Key, API Secret) from your Partner settings page. If you do not see this option, you may not be a Partner Admin role, so for access please contact us at [info@homezada.com](mailto:info@homezada.com).

Authentication of API requests is made using HTTP Basic Authentication. Use your API Key as the user name and your API Secret as the password for Basic Authentication. HTTPS must be used for all API requests.

<aside class="notice">
You must replace <code>PARTNER_ID</code> with your Partner API key and <code>PARTNER_API_SECRET</code> with your Partner API secret in the examples provided.
</aside>

# Versioning

The API is versioned and can be access from the following root address per version:

`/api/v1`

Staging and API sandbox data can be accessed via

[https://staging.homezada.com/api/v1](https://staging.homezada.com/api/v1)

The production data can be accessed via

[https://secure.homezada.com/api/v1](https://secure.homezada.com/api/v1)

# Common Parameters


The JSON API spec provides a set of common query parameters to allow you to easily sort, filter, nest and page data. Examples are provided on the right.

## Sorting
The <code>'sort='</code> parameter is used, using the full type parent.child attribute identifier.

```shell
# Sort by ascending email
curl -i 
-H "Accept: application/vnntent-Type:application/vnd.api+json' 
--user PARTNER_ID:PARTNER_API_SECRET 
https://secure.homezada.com/api/v1/users?sort=email
```
```ruby
# Sort by ascending created data timestamp
require "net/http"
require "uri"
require "json"

HOMEZADA_PARTNER_API_URL = "https://secure.homezada.com/api/v1/properties/123456"
uri = URI.parse(HOMEZADA_PARTNER_API_URL)
params = { sort: "email" }
uri.query = URI.encode_www_form( params )

http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true if uri.scheme == 'https'
request = Net::HTTP::Get.new(uri.request_uri)
request.basic_auth(PARTNER_ID, PARTNER_API_SECRET)

response = http.request(request)
result = JSON.parse(response.body) if response.code == '200'
````

```shell
# Sort by descending property name then country
curl -i 
-H "Accept: application/vnntent-Type:application/vnd.api+json' 
--user PARTNER_ID:PARTNER_API_SECRET 
https://secure.homezada.com/api/v1/properties?sort=-name,country
```

```ruby
# Sort by descending property name then country
require "net/http"
require "uri"
require "json"

HOMEZADA_PARTNER_API_URL = "https://secure.homezada.com/api/v1/properties/123456"
uri = URI.parse(HOMEZADA_PARTNER_API_URL)
params = { sort: "-name,country" }
uri.query = URI.encode_www_form( params )

http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true if uri.scheme == 'https'
request = Net::HTTP::Get.new(uri.request_uri)
request.basic_auth(PARTNER_ID, PARTNER_API_SECRET)

response = http.request(request)
result = JSON.parse(response.body) if response.code == '200'
````
## Pagination

The <code>page[number]=</code> and <code>page[size]=</code> parameters can be used. The default page size (and maximium at this time) is 50.

```shell
# Paging example on users
curl -i 
-H "Accept: application/vnntent-Type:application/vnd.api+json' 
--user PARTNER_ID:PARTNER_API_SECRET 
https://secure.homezada.com/api/v1/users?page[number]=1&page[size]=3
````

```ruby
# Sort by descending property name then country
require "net/http"
require "uri"
require "json"

HOMEZADA_PARTNER_API_URL = "https://secure.homezada.com/api/v1/properties/123456"
uri = URI.parse(HOMEZADA_PARTNER_API_URL)
params = { "page[number]": "1", "page[size]": "3" }
uri.query = URI.encode_www_form( params )

http = Net::HTTP.new(uri.host, uri.port)
http.use_ssl = true if uri.scheme == 'https'
request = Net::HTTP::Get.new(uri.request_uri)
request.basic_auth(PARTNER_ID, PARTNER_API_SECRET)

response = http.request(request)
result = JSON.parse(response.body) if response.code == '200'
````

> The following JSON is returned for a paged request

```json
{
   "data":[
      {
         "id":"1311",
         "type":"users",
         "links":{
            "self":"https://secure.homezada.com/api/v1/users/1311"
         },
         "attributes":{
            "name":"David",
            "email":"ding+sdkexample1@homezada.com"
         },
         "meta":{
            "copyright":"Copyright 2020 - HomeZada Inc.",
            "last_updated_at":"2020-01-08 17:11:03 UTC",
            "created_at":"2010-11-23 00:57:15 UTC"
         }
      },
      {
         "id":"60122",
         "type":"professionals",
         "links":{
            "self":"https://secure.homezada.com/api/v1/professionals/60122"
         },
         "attributes":{
            "name":"David Professional",
            "first-name":"David",
            "last-name":"Professional",
            "email":"ding+sdkexample2@homezada.com",
            "company-name":"UniqueName",
            "phone":"+1 604 307 1131",
            "facebook":"https://facebook.com/1234",
            "twitter":"https://twitter.com/_david_ing",
            "linkedin":"",
            "contact-email":"123@gmail.com",
            "website":"www.test.com",
            "company-market":"Real Estate",
            "industry-license-info":"CalBRE #01039089",
            "company-logo":"https://homezada-dev-env.s3.amazonaws.com/uploads/professional/company_logo/60/clean_all_of_your_small_appliances.jpg",
            "headshot":"https://homezada-dev-env.s3.amazonaws.com/uploads/professional/headshot/60/3.jpg"
         },
         "meta":{
            "copyright":"Copyright 2020 - HomeZada Inc.",
            "last_updated_at":"2019-10-15 02:21:41 UTC",
            "created_at":"2012-10-26 21:48:55 UTC"
         }
      },
      {
         "id":"222",
         "type":"users",
         "links":{
            "self":"https://secure.homezada.com/api/v1/users/222"
         },
         "attributes":{
            "name":"buy gift",
            "email":"ding+sdkexample3@homezada.com"
         },
         "meta":{
            "copyright":"Copyright 2020 - HomeZada Inc.",
            "last_updated_at":"2013-12-10 22:56:33 UTC",
            "created_at":"2013-12-10 22:54:24 UTC"
         }
      },
   ],
   "meta":{
      "record-count":3,
      "page-count":1
   },
   "links":{
      "first":"http://localhost:3000/api/v1/users?page%5Bnumber%5D=1&page%5Bsize%5D=50",
      "last":"http://localhost:3000/api/v1/users?page%5Bnumber%5D=1&page%5Bsize%5D=50"
   }
}
````

# Users

A User is a regular HomeZada consumer account. When created via this API it will be associated with the Partner id automatically.

<aside class="notice">
A new account is created with a random strong password. Please use the Password Reset with the associated email address on the account.
</aside>

## Get All Users

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
curl "http://example.com/api/kittens"
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

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific User

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
curl "http://example.com/api/kittens/2"
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

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific User

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
curl "http://example.com/api/kittens/2"
  -X DELETE
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

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

# Professionals

A Professional is a business oriented HomeZada account. When created via this API it will be associated with the Partner id.

## Get All Professionals


# Properties

A Property is a physical property that belongs to either a User or a Professional. When created via this API it will be associated with the Partner id.

## Get All Properties

# Photos

A Property is a physical property that belongs to either a User or a Professional. When created via this API it will be associated with the Partner id.

## Get All Photos

# Documents

A Property is a physical property that belongs to either a User or a Professional. When created via this API it will be associated with the Partner id.

## Get All Documents