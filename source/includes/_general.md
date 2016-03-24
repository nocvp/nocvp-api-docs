
# General Information

##API Status
Status, issues, and bugs for the API can be found at <a href='http://status.api.nocvp.com/'>status.api.nocvp.com</a>!
##Overview
NOCVP API exposes the entire OVP infrastructure via a standardized programmatic interface. Using NOCVP API, you can do just about anything you can do on dashboard.nocvp.com, while using your programming language of choice.
The NOCVP API is a RESTful API based on HTTP requests and JSON responses. 
This version of the API, version 1, uses OAuth 2.0. This means that all requests will need to be encrypted and sent via SSL/TLS to https://api.nocvp.com. 

##Need help?
The NOCVP engineers are always around answering questions. Send your questions to nocvp-api@noc.com.tr.

##Creating an API Client
In order to use NOCVP API you must create an api client and receive the client_id and client_secret.

##Endpoints
The API is accessed by making HTTP requests to endpoint URL, in which GET or POST variables contain information about what you wish to access. Every endpoint is accessed via an SSL-enabled HTTPS (port 443), this is because everything is using OAuth 2.0.

##Responses
Each response returns a valid json object or array. In case of api returns array X-Total-Count http header can be checked for the total number of objects could be fetched.

##Paging Results
For the most part, if the API action is plural, you can page it via a query string parameter.

Query String Parameter | Required | Description
--------- | ------- | -----------
limit | optional | Limit the number of results per page. (default: 25, max: 250)
offset | optional | Page number of the result set (default: 0)

Example:
https://api.nocvp.com/v1/asset?limit=12&offset=24

#Authentication
The API requires each client to use OAuth 2 authentication. Oauth 2.0 allows a registered application/client to obtain an OAuth 2 Bearer Token, which can be used to make API requests on an application’s own behalf, without a user context. This is called Application-only authentication.

Successful responses include a JSON-structure describing the awarded Bearer Token.

Finally, after obtaining your access_token, you make your API requests by sending the Authorization header as such:

Authorization: Bearer YOUR_ACCESS_TOKEN

## Resource URL

`POST https://api.nocvp.com/oauth`

### Request Parameters

> To get an access token, example request should be as,

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -H "Content-Type: application/json" -d '{
    "grant_type": "client_credentials",
    "client_id": "your client id",
    "client_secret": "your client secret"
}' "https://api.nocvp.com/oauth"
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

`Elements in bold are mandatory.`

Parameter | Default | Description
--------- | ------- | -----------
<b>grant_type</b> | mixed | only client_credentials allowed
<b>client_id</b> | mixed | your client id
<b>client_secret</b> | mixed | your client secret

### Response Parameters

> Successful authorization returns the following json structure.

```json
{
  "access_token": "4cf26d8c6f7baedd69d56c3a1a7a8dcb96bb1234",
  "expires_in": 3600,
  "token_type": "Bearer",
  "scope": null
}
```

Parameter | Default | Description
--------- | ------- | -----------
access_token | mixed | access token
expires_in | mixed | expires seconds
token_type | mixed | Token type is only Bearer supported
scope | null | not implemented

#Error Codes & Responses
##HTTP Status Codes
The NOCVP API attempts to return appropriate HTTP status codes for every request.

Code | Text | Description
-----| ---- | -----------
200 | OK | Success!
304 | Not Modified | There was no data to return.
400 | Bad Request | The request was invalid or cannot be served. An error message will explain further.
401 | Unauthorized | Authentication credentials are missing or incorrect.
403 | Forbidden | The request is understood, but it has been refused or access is not allowed. An error message will explain why.
404 | Not Found | The URI requested is invalid or the resource requested, such as a asset, does not exists.
429 | Too Many Requests | Returned when a request cannot be served due to the application’s rate limit having been exhausted for the resource.
500 | Internal Server Error | Something is broken.
502 | Bad Gateway | API is down or being upgraded.
503 | Service Unavailable | API servers are up, but overloaded with requests. Try again later.
504 | Gateway timeout | API servers are up, but the request couldn’t be serviced due to some failure within our stack. Try again later.

##Error Messages
When the NOCVP API returns error messages, it does so in JSON format. For example, an error might look like on the right side.

```
{
  "type": "Bad Request",
  "title": "Validation Failed",
  "status": 400,
  "detail": {
    "templates": {
      "isEmpty": "Value is required and can't be empty"
    }
  }
}
```