---
title: API Reference

language_tabs:
  - curl

toc_footers:
  - <a href='https://www.white.eu.com'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the White API! You can use our API to access White API endpoints.

# Authentication

> To authorize, use this code:

```curl
# With curl, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: YourApiKey"
```

> Make sure to replace `YourAuthCode` with your API key.

White uses API keys to allow access to the API. You can register a new API key by going in [your application settings](https://app.white.eu.com/application/settings/api).

White expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: YourApiKey`

<aside class="notice">
You must replace <code>YourApiKey</code> with your personal API key.
</aside>

# Invoices

## Generate an invoice

```curl
curl "https://white.technology/api/v1/invoices/create"
  -H "Authorization: YourApiKey"
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

This endpoint creates a new invoice.

### HTTP Request

`PUT https://white.technology/api/v1/invoices/create`

### Query Parameters

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
contact_id | Integer | | ID of the contact the invoice is created to.
value_date | Date | false | Date the invoice is created. Defaults to the date the request is made.
number | String | false | Mandatory if auto number generation is disabled.
due_date | Date | false | Date the invoice is due. Defaults to the date the request is made.
commercial_discount | Float | false | Commercial discount applied to the invoice's total before taxes. e.g. 210.51.
flows_attributes | Array | | The list of lines.
language_id | Integer | | ID of the language used to generate the invoice.
generate_pdf | Boolean | false | If set to `true` White will generate a pdf for the invoice.

Each element of the `flows_attributes` array must be a `Hash` with the following elements:

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
item_id | Integer | | true | ID of the item appearing on the invoice.
quantity | Integer | Float | 1 | false | Number of items `item_id` appearing on the invoice.
unit_price_attributes | Hash | | true | An array representing the price of the item.

A price is a `Hash` that must contain the following elements:

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
inclusive_tax | Float | | false | The `Item` price inclusive tax. Mandatory if `exclusive_tax` is not present.
exclusive_tax | Float | | false | The `Item` price exclusive tax. Mandatory if `inclusive_tax` is not present.
tax_id | Integer | | false | ID of the tax to apply to the `inclusive_tax` or `exclusive_tax`. Mandatory if both `inclusive_tax` and `exclusive_tax` are not provided.
currency_id | Integer | | false | ID of the invoice currency. Not used if `tax_id` is provided.

<aside class="notice">
You can pass both <code>inclusive_tax</code> and <code>exclusive_tax</code>.
</aside>

# Value added taxes (VATs)

## List available VATs

```curl
curl "https://white.technology/api/v1/invoices/create"
  -H "Authorization: YourApiKey"
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

This endpoint lists all the available value added taxes (VAT).

### HTTP Request

`GET https://white.technology/api/v1/vats`

### Query Parameters

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
country | String | | false | The country for which you want to list the available VATs. Returns all the VAT rates for all countries if not present. The expected value must be one of the [ISO_3166-1_alpha-3](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3) values.
date | Date | | false | The date at which you want to list the VATs. Defaults to the date the request was made. Returns all the VAT rates whatever their date if not present.

<aside class="notice">
It sometimes happen that a country changes the rates of its VATs. By providing the date you ensure to get the list of VATs legally accepted at the given date.
</aside>