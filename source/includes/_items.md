# Items

 An item represents a good or a service that you buy, sell or produce.

## Create an item

```curl
curl https://www.white.technology/api/v1/items/create
     -X PUT
     -H "Accept: application/json"
     -H "X-Entity-Token: UserApiKey"
     -H "X-Entity-White-Name: company_white_name"
     -d "name=Access to White API"
     -d "type=service"
```

> The above command returns JSON structured like this:

```json
"{
  \"item\": {
    \"id\": null,
    \"name\": \"Access to White API\",
    \"reference\": null,
    \"internal_id\": null,
    \"type\": \"service\"
  }
}"
```

This endpoint creates a new item.

### HTTP Request

`PUT https://white.technology/api/v1/items/create`

### Query Parameters

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
name | String | | false | The item's name as it will appear on a document (estimate, invoice, etc.).
reference | String | | false | The item's reference as it will appear on a document.
internal_id | String | | false | An ID that you can freely provide to reference the item in your own information system.
type | String | | true | Represents how the item will be dealt with in your books. There are three possible values: good, service, study.

<aside class="notice">
<code>internatl_id</code> is a free parameter that you can provide if you want to find the item in your own database.
</aside>