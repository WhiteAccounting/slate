# Invoices

## Create an invoice

```curl
curl https://www.white.technology/api/v1/invoices/create
     -X PUT
     -H "Accept: application/json"
     -H "X-Entity-Token: UserApiKey"
     -H "X-Entity-White-Name: company_white_name"
     -d "{"contact_id": 57, "language": "fr", "generate_pdf": true,
          "flows_attributes"=[
            {"item_id": 129, "quantity": 1, "unit_price_attributes"=[{"inclusive_tax": 104.5, "tax_id": 6}]}
            {"item_id": 56, "quantity": 5, "unit_price_attributes"=[{"inclusive_tax": 15.1, "tax_id": 6}]}
          ]}"
```

> The above command returns JSON structured like this:

```json
```

This endpoint creates a new invoice.

### HTTP Request

`PUT https://white.technology/api/v1/invoices/create`

### Query Parameters

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
contact_id | Integer | | ID of the contact the invoice is created to.
value_date | Date | | false | Date the invoice is created. Defaults to the date the request is made.
number | String | | false | Mandatory if auto number generation is disabled.
due_date | Date | | false | Date the invoice is due. Defaults to the date the request is made.
commercial_discount | Float | 0 | false | Commercial discount applied to the invoice's total before taxes. e.g. `210.51`.
language | String | | false | The language used to generate the invoice. It must be one of the [ISO 639-1 codes](https://fr.wikipedia.org/wiki/Liste_des_codes_ISO_639-1). Defaults to the language of the country your company is settled in.
generate_pdf | Boolean | false | false | If set to `true`, White will generate a pdf for the invoice.
send_pdf | Boolean | false | false | If set to `true`, White will send the generated pdf.
send_to | Array | | false | | The list of email addresses the generated pdf will be sent to. Mandatory if `send_pdf` is `true`.
flows_attributes | Array | | true | The list of lines (see below).

Each element of the `flows_attributes` array must be a `Hash` with the following elements:

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
item_id | Integer | | true | ID of the item you are selling.
quantity | Float | 1 | false | Number of items `item_id` appearing on the invoice.
unit_price_attributes | Array | | true | An array representing the price of the item.

`unit_price_attributes` is an array of **one** hash that contains the following elements:

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
inclusive_tax | Float | | false | The `Item` price inclusive tax. Mandatory if `exclusive_tax` is not present.
exclusive_tax | Float | | false | The `Item` price exclusive tax. Mandatory if `inclusive_tax` is not present.
tax_id | Integer | | false | ID of the tax to apply to the `inclusive_tax` or `exclusive_tax`. Mandatory if only `inclusive_tax` or `exclusive_tax` is provided.
currency | String | | false | The invoice currency. Not used if `tax_id` is provided. It must be one of the [ISO-4217 codes](https://en.wikipedia.org/wiki/ISO_4217).

<aside class="notice">
Most of the time you will use one of these combinations to create a price:
 <ul>
 <li><code>exclusive_tax</code>, <code>tax_id</code> (<code>currency</code> is optional).</li>
 <li><code>inclusive_tax</code>, <code>tax_id</code> (<code>currency</code> is optional).</li>
 <li><code>inclusive_tax</code>, <code>exclusive_tax</code> and <code>currency</code>. </li>
 </ul>
</aside>