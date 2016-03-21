---
title: NOCVP API Reference

language_tabs:
  - shell
  - http

toc_footers:
  - <a href='http://dashboard.nocvp.com/'>Dashboard</a>

includes:
  - add_media

search: true
---

# Introduction

Welcome!

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -H "Content-Type: application/json" -d '{
    "grant_type": "client_credentials",
    "client_id": "your client id",
    "client_secret": "your client secret"
}' "http://api.nocvp.com/oauth"
```

```http
POST /oauth HTTP/1.1
Host: api.nocvp.com
Content-Type: application/json

{
    "grant_type": "client_credentials",
    "client_id": "your client id",
    "client_secret": "your client secret"
}
```


NOCVP uses API keys to allow access to the API. You can register a new NOCVP API key at our [dashboard portal](http://dashboard.nocvp.com/).

NOCVP expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: nocvpapikey`

<aside class="notice">
You must replace <code>nocvpapikey</code> with your personal API key.
</aside>

