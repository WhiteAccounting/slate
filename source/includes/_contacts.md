# Contacts

A contact represent a company or person you do business with.

## Create a contact

```curl
curl "https://white.technology/api/v1/contacts/create"
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

This endpoint creates a new contact.

### HTTP Request

`PUT https://white.technology/api/v1/contacts/create`

### Query Parameters

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
name | String | | false | The contact's name.
email | String | | false | The contact's email.
address | String | | false | The contact's address.
zip_code | String | | false | The contact's zip code.
city | String | | false | The contact's city.
tel | String | | false | The contact's telephone.
national_number | String | | false | The contact's unique identifier in its country. That is different from the VAT number (below). For instance in France the national number is the [Siret number](https://fr.wikipedia.org/wiki/Syst%C3%A8me_d%27identification_du_r%C3%A9pertoire_des_%C3%A9tablissements).
vat_number | String | | false | The contact's [VAT number](https://en.wikipedia.org/wiki/VAT_identification_number).
external_id | String | | false | An ID that you can freely provide to reference the contact in your own information system.
country | String | | true | The contact's country. The value must be a [ISO 3166-1 alpha-3 code](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3).

<aside class="notice">
<code>External_id</code> is a free parameter that you can provide if you want to find the contact in your own database.
</aside>