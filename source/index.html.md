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

## HTTP Request

`POST http://api.nocvp.com/oauth`

### Query Parameters


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

> The above command returns JSON structured like this:

```json
{
  "access_token": "4cf26d8c6f7baedd69d56c3a1a7a8dcb96bb1234",
  "expires_in": 3600,
  "token_type": "Bearer",
  "scope": null
}
```

`Elements in bold are mandatory. Attributes in bold are mandatory only if Element is present, default value is shown after equals sign.`

Parameter | Default | Description
--------- | ------- | -----------
<b>grant_type</b> | mixed | only client_credentials allowed
<b>client_id</b> | mixed | your client id
<b>client_secret</b> | mixed | your client secret

### Response Parameters

Parameter | Default | Description
--------- | ------- | -----------
access_token | mixed | access token
expires_in | mixed | expires seconds
token_type | mixed | Token type is only Bearer supported
scope | null | not implemented


NOCVP uses API keys to allow access to the API. You can register a new NOCVP API key at our [dashboard portal](http://dashboard.nocvp.com/).

NOCVP expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer 4cf26d8c6f7baedd69d56c3a1a7a8dcb96bb1234`
