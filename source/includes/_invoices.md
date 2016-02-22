# Invoices

## Create an invoice

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
language | String | | The language used to generate the invoice. It must be one of the [ISO 639-1 codes](https://fr.wikipedia.org/wiki/Liste_des_codes_ISO_639-1).
generate_pdf | Boolean | false | If set to `true` White will generate a pdf for the invoice.

Each element of the `flows_attributes` array must be a `Hash` with the following elements:

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
item_id | Integer | | true | ID of the item appearing on the invoice.
quantity | Float | 1 | false | Number of items `item_id` appearing on the invoice.
unit_price_attributes | Hash | | true | An array representing the price of the item.

A price is a `Hash` that must contain the following elements:

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
inclusive_tax | Float | | false | The `Item` price inclusive tax. Mandatory if `exclusive_tax` is not present.
exclusive_tax | Float | | false | The `Item` price exclusive tax. Mandatory if `inclusive_tax` is not present.
tax_id | Integer | | false | ID of the tax to apply to the `inclusive_tax` or `exclusive_tax`. Mandatory if both `inclusive_tax` and `exclusive_tax` are not provided.
currency | String | | false | The invoice currency. Not used if `tax_id` is provided. It must be one of the [ISO-4217 codes](https://en.wikipedia.org/wiki/ISO_4217).

<aside class="notice">
You can pass both <code>inclusive_tax</code> and <code>exclusive_tax</code>.
</aside>