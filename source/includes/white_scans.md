# White Scans

## Creating a WhiteScan from a document will generate a transaction and associated bookings-

> The above command returns JSON structured like this:

### HTTP Request

`POST https://white.technology/api/v1/vats`

### Query Parameters

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
file | File | | true | The file to process
provider | Boolean | | true | Set to `true` if the document is from a provider. Set to `false` if the document is for a client.