---
title: NOCVP API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='http://dashboard.nocvp.com/'>Dashboard</a>

includes:
  - add_media
  - asset
  - category
  - playlist
  - player
  - template_group
  - advertisement
  - user
  - client
  - errors

search: true
---

# Introduction

Welcome!

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: nocvpapikey"
```

> Make sure to replace `nocvpapikey` with your API key.

NOCVP uses API keys to allow access to the API. You can register a new NOCVP API key at our [dashboard portal](http://dashboard.nocvp.com/).

NOCVP expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: nocvpapikey`

<aside class="notice">
You must replace <code>nocvpapikey</code> with your personal API key.
</aside>

