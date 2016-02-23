# Value added taxes (VATs)

## List available VATs

```curl
curl "https://white.technology/api/v1/vats"
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
country | String | | false | The country for which you want to list the available VATs. Returns all the VAT rates for all countries if not present. The value must be a [ISO 3166-1 alpha-3 code](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-3).
date | Date | | false | The date at which you want to list the VATs. Defaults to the date the request is made. Returns all the VAT rates whatever their date if not present.

<aside class="notice">
It sometimes happen that a country changes the rates of its VATs. By providing the date you ensure to get the list of VATs legally accepted at the given date.
</aside>