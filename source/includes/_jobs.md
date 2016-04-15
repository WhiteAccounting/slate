# Jobs

We call a `job` the task of processing a document to read, qualify and book it. You can create `jobs` through our API and
retrieve their results.

A job cannot be destroyed.

## Creating a job

```ruby
require 'faraday'

@conn = Faraday.new(:url => 'http://kpmg.white.technology') do |faraday|
  faraday.request :multipart # To send files
  faraday.adapter :net_http  # To send files
end

@payload = { :file => Faraday::UploadIO.new('file.pdf', 'application/pdf'),
             :provider => true  # The file is coming from one of our providers
           }

@query = @conn.post 'api/v1/:organization/jobs.json',
                    @payload,
                    { 'Authorization' => "Bearer ACCESS_TOKEN" }

```

> The above command returns JSON structured like this:

```json
{
  "id": "55bb001fb9b8464ca2d23ac8449f269c"
}
```

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

The returned object has a `processed` boolean field stating if the job has been processed or is still queued.

Processed | Status | Returned object
--------- | ---- | --------
false | Queued | All values of the returned object are null.
true | Processed | The values of the object are filled.


```shell
  curl -H "Authorization: Bearer ACCESS_TOKEN" \
       -X GET \
       http://kpmg.white.technology/api/v1/:organization/jobs/:id.json
```

```ruby

  @faraday = Faraday.new(:url => 'http://kpmg.white.technology') do |faraday|
    faraday.request :url_encoded
    faraday.adapter Faraday.default_adapter
  end

  @response = @faraday.get 'api/v1/:organization/jobs/:id.json'
```

> The above command returns JSON structured like this:

```json
{
  "job": {
    "id": "34d5b9b3c2fe4752b35fcbb5ebb7f6f3",
    "tag": "etude_et_prestation_de_service",
    "document_type": "invoice",
    "value_date": null,
    "currency": "EUR",
    "name": "John Lennon",
    "address": "78 boulevard Voltaire",
    "zip_code": "75011",
    "city": "Paris",
    "email": "john.lennon@gmail.com",
    "tel": "0101010101",
    "vat_number": null,
    "national_number": null,
    "prices": [
      {
        "inclusive_tax": 250.0,
        "exclusive_tax": 238.41
      }],
    "processed": true
  }
}
```

### HTTP Request

`GET http://kpmg.white.technology/api/v1/:organization/jobs/:id`

### Query Parameters

Parameter | Type | Default | Required | Description
--------- | ---- | --------| -------- | -----------
id | String | | true | The id of the job (as returned by the server at job creation)

