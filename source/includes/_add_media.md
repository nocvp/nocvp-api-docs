# Add Media
NOCVP supports a couple of media ingestion methods, upload by file and upload by url are the most used ones. In order to upload a file you need to get an upload url with a token first. Then using this upload token is required while sending http post request to our upload servers with the contents of the file in the request body. Resumable uploads are also supported.

There are some possible options while getting the upload url, please investigate the query parameters below.

## File Upload

### Step 1. Get Upload Url

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -H "Authorization: Bearer 6bb258814327c7a9ef0790590d6cc8269c7526ce" -H "Content-Type: application/json" -d '{
    "jobStatusCallBackUrl" : "https://your_jobs_status_callBackUrl",
    "replacesAssetId" : "56efe5e386ec3526220041a9",
    "privacy": "PUBLIC",
    "templates": [
        "552f6c54d67248840f8b4511"
    ],
    "templateGroupOptions": {
        "textLine1" : {
            "text" : "This should be seen on the video 111."
        },
        "textLine2" : {
            "text" : "This should be seen on the video 222."
        }
    }
}' "https://api.nocvp.com/v1/upload"
```

```http
POST /v1/upload HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 6bb258814327c7a9ef0790590d6cc8269c751111
Content-Type: application/json

{
    "jobStatusCallBackUrl" : "https://your call back url",
    "replacesAssetId" : "56efe5e386ec3526220041a9",
    "privacy": "PUBLIC",
    "templates": [
        "552f6c54d67248840f8b4511"
    ],
    "templateGroupOptions": {
        "textLine1" : {
            "text" : "This should be seen on the video 111."
        },
        "textLine2" : {
            "text" : "This should be seen on the video 222."
        }
    }
}
```

> The above command returns JSON structured like this:

```json
{
  "url": "http://upload.nocvp.com/upload?token=56efe5e386ec3526220041a9"
}
```

#### HTTP Request

`POST http://api.nocvp.com/v1/upload`

#### Query Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
replacesAssetId | string | this parameter is used to support asset source change, input should be a valid asset id, this asset is going to be replaced by the one you will upload.
jobStatusCallBackUrl | url | this parameter is used in case you want to receive transcoding job status updates, api will send POST requests with a body indicating the job status. <a href="/?shell#transcoding-job-notification-object-structure"> Check for a sample one</a> .
isPoster | boolean | must be true for asset or category poster uploading.
category | string | Asset category id if required when category poster uploading.
asset | string | Asset id if required when asset poster uploading.
privacy | string | PUBLIC or PRIVATE.
templateGroupOptions | <a href="/?shell#template-group-options-structure">templateGroupOptions</a> | overriding 
                                                                                                  template group options
templates | array | Template group ids.

#### Response Parameters

Parameter | Type | Description
--------- | ------- | -----------
url | mixed | url for upload

### Step 2. Upload the file
The video can actually be uploaded to the upload url retrieved above by making a POST HTTP request.

```shell
curl 'your_upload_url_with_token' -X POST
   -H 'Content-Disposition: attachment; filename="your_file.mp4"' 
   --data-binary @your_file.mp4
```

```http
POST /upload?token=56f2918700ddb349078b5040 HTTP/1.1
Host: upload.nocvp.com
Content-Disposition: attachment; filename="your_file.mp4"

<bytes 0-51200>
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

#### Response Parameters

Parameter | Type | Description
--------- | ------- | -----------
success | boolean | 1|0
title | mixed | Asset Title
detail.id | mixed | Asset Id
detail.sid | mixed | Asset Short Id



## Upload By Url
This method supports fetching from an http server and major video sites like youtube, vimeo, etc.

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -H "Authorization: Bearer 6bb258814327c7a9ef0790590d6cc8269c7526ce" -H "Content-Type: application/json" -d '{
    "jobStatusCallBackUrl" : "https://your call back url",
    "replacesAssetId" : "56efe5e386ec3526220041a9",
    "url" : "https://www.youtube.com/watch?v=XXE-I89CG6s",
    "privacy": "PUBLIC",
    "templates": [
        "552f6c54d67248840f8b4511"
    ],
    "templateGroupOptions": {
        "textLine1" : {
            "text" : "This should be seen on the video 111."
        },
        "textLine2" : {
            "text" : "This should be seen on the video 222."
        }
    }
}' "http://api.nocvp.com/v1/upload-from-url"
```

```http
POST /v1/upload-from-url HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 6bb258814327c7a9ef0790590d6cc8269c751111
Content-Type: application/json

{
    "jobStatusCallBackUrl" : "https://your call back url",
    "replacesAssetId" : "56efe5e386ec3526220041a9",
    "url" : "https://www.youtube.com/watch?v=XXE-I89CG6s",
    "privacy": "PUBLIC|PRIVATE",
    "templates": [
        "552f6c54d67248840f8b4511"
    ],
    "templateGroupOptions": {
        "textLine1" : {
            "text" : "This should be seen on the video 111."
        },
        "textLine2" : {
            "text" : "This should be seen on the video 222."
        }
    }
}
```

> The above command returns JSON structured like this:

```json
{
  "sid": "7B994oKn",
  "id": "56eff00986ec35081a0041a9"
}
```

#### HTTP Request

`POST http://api.nocvp.com/v1/upload-from-url`

#### Query Parameters
`Elements in bold are mandatory.`

Parameter | Type | Description
--------- | ------- | -----------
replacesAssetId | string | this parameter is used to support asset source change and retranscding, input a valid asset id, this asset is going to be replaced by the one you will upload.
jobStatusCallBackUrl | url | this parameter is used in case you want to receive transcoding job status updates, api will send POST requests with a body indicating the job status. <a href="/?shell#transcoding-job-notification-object-structure"> Check for a sample one</a> .
<b>url</b> | mixed | youtube, daily motion, direct url ...etc
privacy | string | PUBLIC or PRIVATE.
templateGroupOptions | <a href="/?shell#template-group-options-structure">templateGroupOptions</a> | overriding 
template group options
templates | array | Template group ids.

#### Response Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | mixed | Asset Id
sid | mixed | Asset Short Id


## Create Live Stream

## Create Live Event