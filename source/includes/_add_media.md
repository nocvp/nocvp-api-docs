
# Add Media

## Upload URL

### Get Upload URL
```shell
curl 'http://api.nocvp.com/v1/upload' -X POST
-H 'Content-Type: application/json;charset=utf-8'
-H 'Authorization: Bearer 2611f787760c1ebcd7e75aa36d22da55069cf1a3'
-d '{"templates":["56e70a8100ddb33d5c8b4b0f"],"privacy":"PUBLIC","category":"55c49e4000ddb315158b7801","templateGroupOptions"
:{"textLine1":{"text":"Test"},"textLine2":{"text":"Test2"}}}'
```

> The above command returns JSON structured like this:

```json
{
   "path":null,
   "asset":null,
   "account":{
      "id":"55546c1c00ddb386548b456a",
      "playerDomains":null,
      "deliveryStatus":"ACTIVE"
   },
   "client":null,
   "creationTime":1458309226,
   "id":"56ec086a00ddb376068b458a",
   "url":"http://upload.nocvp.com/upload?token=56ec086a00fsb376068b458a",
   "user":{
      "id":"55546c1c00ddb386548b456f"
   },
   "isPoster":false,
   "category":{
      "id":"55c49e4000ddb315158b7801",
      "title":"Kategori 2"
   },
   "templates":[
      "56e70a8100ddb33d5c8b4b0f"
   ],
   "privacy":"PUBLIC",
   "templateGroupOptions":{

   }
}
```

You must get a new upload url for local file upload.

#### HTTP Request

`POST http://api.nocvp.com/v1/upload`

#### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
category | string | Asset category id.
privacy | string | PUBLIC or PRIVATE.
templateGroupOptions | hash | templateGroupOptions.
templates | array | Template group ids.


### Upload Your File

```shell
curl 'upload_url' -X POST
-H 'Content-Type: video/mp4'
-H 'Content-Disposition: attachment; filename="yourfile.mp4"'
```

> The above command returns JSON structured like this:

```json
{
   "success":1,
   "title":"File uploaded!",
   "detail":{
      "id":"56ec1b6400ddb3e5358b457f",
      "sid":"7B5jdGpt"
   }
}
```
After you get the upload url, you can directly POST your file to this url.

## Import from Direct URL

## Create Live Streaming

## Create Event

