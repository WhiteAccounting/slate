---
title: API Reference

language_tabs:
  - shell
  - ruby

toc_footers:
  - <a href='https://www.white.technology'>Sign Up for a developer key</a>

includes:
  - organizations
  - jobs

search: true
---

<!---
  - contacts
  - items
  - invoices
  - vats
  - currencies
  - countries
  - languages
  - white_scans
  - errors
--->

# Introduction

Welcome to the **White** API documentation! You will find here everything there is to know about our API. Don't hesitate to [get in touch](mailto:support@white.eu.com) if that is not enough.

Have fun.

# Authorization

> Example of authorization process

```shell
#!/usr/bin/env bash

# Get the authorization code

curl -X POST \
  -H "Content-Type: application/json" \
  -d "{\"client_id\":\"CLIENT_ID\", \
       \"client_secret\":\"CLIENT_SECRET\", \
       \"redirect_uri\":\"REDIRECT_URI\", \
       \"response_type\":\"code\"}" \
  http://kpmg.white.technology/api/oauth/authorize.json

# Get the access token

curl -X POST \
  -H "Content-Type: application/json" \
  -d "{\"client_id\":\"CLIENT_ID\", \
       \"client_secret\":\"CLIENT_SECRET\", \
       \"redirect_uri\":\"REDIRECT_URI\", \
       \"code\":\"CODE\", \
       \"grant_type\":\"authorization_code\"}" \
  http://kpmg.white.technology/api/oauth/token.json
```


```ruby
gem install 'faraday' # Without bundler
gem 'faraday' # With bundler (Gemfile)

require 'faraday'

faraday = Faraday.new(:url => 'http://kpmg.white.technology') do |faraday|
            faraday.request :url_encoded
            faraday.adapter Faraday.default_adapter
          end

response = faraday.post 'api/oauth/authorize.json',
                      {
                          :client_id => CLIENT_ID,          # Ask us for yours
                          :client_secret => CLIENT_SECRET,  # Ask us for yours
                          :redirect_uri => REDIRECT_URI,    # Must be https/ssl!
                          :response_type => 'code'
                      }

code = JSON.parse(response.body)['code']

response = @conn.post 'api/oauth/token.json',
                      {
                          :client_id => CLIENT_ID,          # Same as above
                          :client_secret => CLIENT_SECRET,  # Same as above
                          :redirect_uri  => REDIRECT_URI,   # Same as above
                          :code => code,                    # Result of previous request
                          :grant_type => 'authorization_code'
                      }

token = JSON.parse(@response.body)

```

**White** uses an [OAuth2](http://oauth.net/2/) authorization / authentication protocol to grant access to the API.

The authentication takes an `access token` that must be provided in the header of every request.

`
 "Authorization: Bearer ACCESS_TOKEN"
`

example:

`
 "Authorization: Bearer 14q1506268bed878972b42e9f99154f37ef9a214042542782c54e946ce845a64"
`

To obtain your `access token`, you need to

  1. Request a new `client_id` / `client_secret` pair in [your application settings](https://app.white.technology/application/settings/api).
  2. Use this code pair to get an authorization code.
  3. Use the authorization code to get an `access token`.

<aside class="notice">
<ol>
 <li>Access tokens are bound to users. If you wish to give different acces to <bold>White</bold> for different users you are welcome to do so by giving each user a different key.</li>
 <li>Even though our <code>access tokens</code> do not expire, you can revoke them or request a new one at any moment.</li>
<ol>
</aside>

Numerous libraries exist in every language to acquire OAuth2 access tokens. You are free to use any of them.
