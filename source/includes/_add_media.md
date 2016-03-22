# Add Media

## Get Unique Upload URL

### Upload by Local Storage

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -H "Authorization: Bearer 6bb258814327c7a9ef0790590d6cc8269c7526ce" -H "Content-Type: application/json" -d '{
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
}' "http://api.nocvp.com/v1/upload"
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

`Elements in bold are mandatory. Attributes in bold are mandatory only if Element is present, default value is shown after equals sign.`

Parameter | Default | Description
--------- | ------- | -----------
replacesAssetId | valid asset id mixed | if you want replace asset when transcoding completed
jobStatusCallBackUrl | valid url | your call back url for job status updating
isPoster | boolean | must be true for asset or category poster uploading.
category | string | Asset category id if required when category poster uploading.
asset | string | Asset id if required when asset poster uploading.
privacy | string | PUBLIC or PRIVATE.
templateGroupOptions | <a href="/?shell#template-group-options-structure">templateGroupOptions</a> | overriding 
                                                                                                  template group options
templates | array | Template group ids.

#### Response Parameters

Parameter | Default | Description
--------- | ------- | -----------
url | mixed | url for upload

### Upload by youtube, daily motion, url ..etc

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
`Elements in bold are mandatory. Attributes in bold are mandatory only if Element is present, default value is shown after equals sign.`

Parameter | Default | Description
--------- | ------- | -----------
replacesAssetId | valid asset id mixed | if you want replace asset when transcoding completed
jobStatusCallBackUrl | valid url | your call back url for job status updating
<b>url</b> | mixed | youtube, daily motion, direct url ...etc
privacy | string | PUBLIC or PRIVATE.
templateGroupOptions | <a href="/?shell#template-group-options-structure">templateGroupOptions</a> | overriding 
template group options
templates | array | Template group ids.

#### Response Parameters

Parameter | Default | Description
--------- | ------- | -----------
id | mixed | Asset Id
sid | mixed | Asset Short Id

## Upload Your File

```shell
curl 'your upload url' -X POST
-H 'Content-Type: video/mp4'
-H 'Content-Disposition: attachment; filename="your_file.mp4"' 
-d @your_file.mp4
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

Parameter | Default | Description
--------- | ------- | -----------
success | boolean | 1|0
title | mixed | Asset Title
detail.id | mixed | Asset Id
detail.sid | mixed | Asset Short Id

## Create Live Stream

## Create Live Event

# Models

## Template Group Options Structure

```json
{
        "prefixAssetSid" : "xqwe32a", 
        "postfixAssetSid" : "xqwe32q", 
        "overlayImages" : [
            {
                "assetSid" : "xcz243S",
                "location" : "TOP_LEFT"
            },
            {
                "assetSid" : "xcz243S",
                "location" : "TOP_RIGHT"
            }
        ],
        "textLine1" : {
            "backgroundColor" : null,
            "backgroundImageAssetSid" : "xcvxds21",
            "opacity" : 0.8,
            "fontColor" : "pink",
            "text" : "This should be seen on the video 111."
        },
        "textLine2" : {
            "backgroundColor" : null,
            "backgroundImageAssetSid" : "xcvxds21",
            "opacity" : 0.8,
            "fontColor" : "pink",
            "text" : "This should be seen on the video 222."
        }
    }
```

Parameter | Default | Description
--------- | ------- | -----------
prefixAssetSid | mixed | asset sid for prefix
postfixAssetSid | mixed | asset sid for postfix
overlayImages[].assetSid | mixed | image asset sid
overlayImages[].location | enumerated | TOP_LEFT,TOP_RIGHT,BOTTOM_LEFT,BOTTOM_RIGHT
textLine1.backgroundColor | mixed | color code
textLine1.backgroundImageAssetSid | mixed | image asset sid
textLine1.opacity | float | text opacity between 0.1 - 1
textLine1.fontColor | mixed | color code
textLine1.text | mixed | your text here
textLine2.backgroundColor | mixed | color code
textLine2.backgroundImageAssetSid | mixed | image asset sid
textLine2.opacity | float | text opacity between 0.1 - 1
textLine2.fontColor | mixed | color code
textLine2.text | mixed | your text here
