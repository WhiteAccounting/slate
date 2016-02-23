# Value added taxes (VATs)

## List available VATs

```curl
curl -G https://www.white.technology/api/v1/vats
     -H "Accept: application/json"
     -H "X-Entity-Token: UserApiKey"
     -H "X-Entity-White-Name: company_white_name"
     -d "country=FRA"
```

> The above command returns JSON structured like this:

```json
"{
  \"vats\": [
    {
      \"id\": 1,
      \"name\": \"Taux zero\",
      \"value_date\": \"1970-01-01\",
      \"rate\": \"0.0\",
      \"default\": false,
      \"country\": \"FRA\"
    },
    {
      \"id\": 2,
      \"name\": \"Taux r\u00e9duit\",
      \"value_date\": \"1982-01-01\",
      \"rate\": \"0.055\",
      \"default\": false,
      \"country\": \"FRA\"
    },
    {
      \"id\": 3,
      \"name\": \"Taux super-r\u00e9duit\",
      \"value_date\": \"1992-01-01\",
      \"rate\": \"0.021\",
      \"default\": false,
      \"country\": \"FRA\"
    },
    {
      \"id\": 4,
      \"name\": \"Taux normal\",
      \"value_date\": \"2000-01-01\",
      \"rate\": \"0.196\",
      \"default\": true,
      \"country\": \"FRA\"
    },
    {
      \"id\": 5,
      \"name\": \"Taux interm\u00e9diaire\",
      \"value_date\": \"2012-01-01\",
      \"rate\": \"0.07\",
      \"default\": false,
      \"country\": \"FRA\"
    },
    {
      \"id\": 6,
      \"name\": \"Taux normal\",
      \"value_date\": \"2014-01-01\",
      \"rate\": \"0.2\",
      \"default\": true,
      \"country\": \"FRA\"
    },
    {
      \"id\": 7,
      \"name\": \"Taux interm\u00e9diaire\",
      \"value_date\": \"2014-01-01\",
      \"rate\": \"0.1\",
      \"default\": false,
      \"country\": \"FRA\"
    },
    {
      \"id\": 8,
      \"name\": \"Pas de TVA \/ TVA non applicable\",
      \"value_date\": \"1900-01-01\",
      \"rate\": null,
      \"default\": false,
      \"country\": \"FRA\"
    }
  ]
}"
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