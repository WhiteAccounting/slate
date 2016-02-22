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

Welcome to the White API! You can use our API to access White API endpoints.

# Authentication

> To authorize, use this code:

```curl
# With curl, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: YourApiKey"
```

> Make sure to replace `YourAuthCode` with your API key.

White uses API keys to allow access to the API. You can register a new API key by going in [your application settings](https://app.white.eu.com/application/settings/api).

White expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: YourApiKey`

<aside class="notice">
You must replace <code>YourApiKey</code> with your personal API key.
</aside>