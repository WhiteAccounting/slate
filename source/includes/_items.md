# Items

 An item represents a good or a service that you buy, sell or produce.

## Create an item

```curl
curl "https://white.technology/api/v1/items/create"
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

This endpoint creates a new item.

### HTTP Request

`PUT https://white.technology/api/v1/items/create`

### Query Parameters

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
name | String | | false | The item's name as it will appear on a document (estimate, invoice, etc.)
external_id | String | | false | An ID that you can freely provide to reference the item in your own information system.
type | String | | true | Represents how the item will be dealt with in your books. There are three possible values: good, service, study.

<aside class="notice">
<code>External_id</code> is a free parameter that you can provide if you want to find the item in your own database.
</aside>