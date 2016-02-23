---
title: API Reference

language_tabs:
  - curl

toc_footers:
  - <a href='https://www.white.eu.com'>Sign Up for a Developer Key</a>

includes:
  - contacts
  - items
  - invoices
  - vats
  - currencies
  - countries
  - languages
  - errors

search: true
---

# Introduction

Welcome to the White API! You will find here everything there is to know about the endpoints
we give you access to and how to use them.

Have fun.

# Authentication

> Example of request with the right set of headers:

```curl
curl https://www.white.technology/api/v1/invoices/create
     -X POST
     -H "Accept: application/json"
     -H "X-Entity-Token: evdsa9b5pi8uww8n38cmpowzi6orxs7b0jrdywuy"
     -H "X-Entity-White-Name: white"
```

White uses API keys to allow access to the API. Each user has an API key. This allows you to keep operations/resources
linked to the users they concern.

For instance, if you plan on booking sales invoices, passing the right API key for the user that made the sale will
allow you to have a breakdown of your sales by user.

If you only need one global access, you are free to use the same API key everywhere.
Since you can create as many users as you want, we recommend creating a user dedicated to the API to differentiate
the operations made through the API from the ones made through the web application.

You can register a new API key by going in [your application settings](https://app.white.eu.com/application/settings/api).

White expects the API key to be included in each API request along with the `white_name` of your organization:

`
 X-Entity-Token: YourApiKey
 X-Entity-White-Name: white_name
`

<aside class="notice">
You must replace <code>YourApiKey</code> with your personal API key.
You must replace <code>white_name</code> with the unique name of your organization in White.
</aside>