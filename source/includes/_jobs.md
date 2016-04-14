# Jobs

We call a `job` the task of processing a document to read, qualify and book it. You can create `jobs` through our API and
retrieve their results.

A job cannot be destroyed.

## Creating a job

> The above command returns JSON structured like this:

### HTTP Request

`POST http://kpmg.white.technology/api/v1/:organization/jobs`

### Query Parameters

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
file | File | | true | The file to process
provider | Boolean | | true | Set to `true` if the document is from a provider. Set to `false` if the document is for a client.
id | String | | false | A possible ID to refer to the job later on. If none is passed, an ID is generated. The ID, whether passed or not is returned in the reply.

<aside class="notice">
If you provide an <code>id</code>, it must be unique to the organization or the request will be rejected.
</aside>

## Retrieving a job

You can retrieve the result of a job with its `id`.

> The above command returns JSON structured like this:

### HTTP Request

`GET http://kpmg.white.technology/api/v1/:organization/jobs/:id`

### Query Parameters

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
id | String | | true | The id of the job (as returned by the server at job creation)