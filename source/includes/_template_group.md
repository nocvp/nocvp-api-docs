# Template Group

## List Template Group

```shell
# With shell, you can just pass the correct header with each request
curl -X GET -H "Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6"
 "https://api.nocvp.com/v1/template-group[/:id]/?queryStringParameters"
```

```http
GET /v1/template-group[/:id]/?queryStringParameters HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6
```

> The above command returns JSON structured like this:

```json
[
  {
      "id": "56e1610786ec352a030041ab",
      "name": "Template Group 1",
      "templates": [
        {
          "type": "IMAGE",
          "singleSnapshotSecond": 12,
          "snapshotIntervalSecond": 20,
          "stripeIntervalSecond": 5,
          "snapshotCount": 5,
          "maxHeight": 320,
          "maxWidth": 480,
          "container": "h264"
        }
      ],
      "useByDefault": false,
      "options": {
        "prefixAssetSid": "xqwe32a",
        "postfixAssetSid": "xqwe32q",
        "overlayImages": [
          {
            "assetSid": "xcz243S",
            "location": "TOP_LEFT"
          },
          {
            "assetSid": "xcz243S",
            "location": "TOP_RIGHT"
          }
        ],
        "textLine1": {
          "backgroundColor": null,
          "backgroundImageAssetSid": "xcvxds21",
          "opacity": "0.8",
          "fontColor": "pink",
          "text": "This should be seen on the video 111.",
          "marquee": false
        },
        "textLine2": {
          "backgroundColor": null,
          "backgroundImageAssetSid": "xcvxds21",
          "opacity": "0.8",
          "fontColor": "pink",
          "text": "This should be seen on the video 222.",
          "marquee": false
        }
      },
      "creationTime": 1457611015480,
  }
]
```

#### HTTP Request

`GET /v1/template-group[/:id]/?queryStringParameters`

#### Query String Parameters

Parameter | Type | Description
--------- | ------- | -----------
limit | integer | Limit of template-group list. Min 1, Max 200
offset | integer | offset of template-group list.

#### Response Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | string | template group id
name | string | template group title
useByDefault | boolean | use by default option
templates | array | <a href="/#video-transcoding-template-object-structure">videoConversionTemplate</a>, <a href="/#audio-transcoding-template-object-structure">audioConversionTemplate</a> or <a href="/#image-transcoding-template-object-structure">imageConversionTemplate</a> each one
options | object | <a href="/#template-group-options-structure">templateGroupOptionsObject</a>
creationTime | long | creation time of milliseconds

## Create Template Group

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
-d '{
      "name": "Template Group 1",
      "templates": [
    	{
    	  "type": "IMAGE",
    	  "singleSnapshotSecond": 12,
    	  "snapshotIntervalSecond": 20,
    	  "stripeIntervalSecond": 5,
    	  "snapshotCount": 5,
    	  "maxHeight": 320,
    	  "maxWidth": 480,
    	  "container": "h264"
    	}
      ],
      "useByDefault": false,
      "options": {
    	"prefixAssetSid": "xqwe32a",
    	"postfixAssetSid": "xqwe32q",
    	"overlayImages": [
    	  {
    		"assetSid": "xcz243S",
    		"location": "TOP_LEFT"
    	  },
    	  {
    		"assetSid": "xcz243S",
    		"location": "TOP_RIGHT"
    	  }
    	],
    	"textLine1": {
    	  "backgroundColor": null,
    	  "backgroundImageAssetSid": "xcvxds21",
    	  "opacity": "0.8",
    	  "fontColor": "pink",
    	  "text": "This should be seen on the video 111.",
    	  "marquee": false
    	},
    	"textLine2": {
    	  "backgroundColor": null,
    	  "backgroundImageAssetSid": "xcvxds21",
    	  "opacity": "0.8",
    	  "fontColor": "pink",
    	  "text": "This should be seen on the video 222.",
    	  "marquee": false
    	}
      }
    }' "https://api.nocvp.com/v1/template-group"
```

```http
POST /v1/template-group HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
  "name": "Template Group 1",
  "templates": [
	{
	  "type": "IMAGE",
	  "singleSnapshotSecond": 12,
	  "snapshotIntervalSecond": 20,
	  "stripeIntervalSecond": 5,
	  "snapshotCount": 5,
	  "maxHeight": 320,
	  "maxWidth": 480,
	  "container": "h264"
	}
  ],
  "useByDefault": false,
  "options": {
	"prefixAssetSid": "xqwe32a",
	"postfixAssetSid": "xqwe32q",
	"overlayImages": [
	  {
		"assetSid": "xcz243S",
		"location": "TOP_LEFT"
	  },
	  {
		"assetSid": "xcz243S",
		"location": "TOP_RIGHT"
	  }
	],
	"textLine1": {
	  "backgroundColor": null,
	  "backgroundImageAssetSid": "xcvxds21",
	  "opacity": "0.8",
	  "fontColor": "pink",
	  "text": "This should be seen on the video 111.",
	  "marquee": false
	},
	"textLine2": {
	  "backgroundColor": null,
	  "backgroundImageAssetSid": "xcvxds21",
	  "opacity": "0.8",
	  "fontColor": "pink",
	  "text": "This should be seen on the video 222.",
	  "marquee": false
	}
  }
}
```

> The above command returns JSON structured to <a href="/#list-template-group">Template Group Object</a>:

#### HTTP Request

`POST https://api.nocvp.com/v1/template-group`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>name</b> | string | template group title
useByDefault | boolean | use by default option
templates | array | <a href="/#video-transcoding-template-object-structure">videoConversionTemplate</a>, <a href="/#audio-transcoding-template-object-structure">audioConversionTemplate</a> or <a href="/#image-transcoding-template-object-structure">imageConversionTemplate</a> each one
options | object | <a href="/#template-group-options-structure">templateGroupOptionsObject</a>

#### Response Parameters

The Response likes <a href="/#list-template-group">Template Group Object</a>


## Update Template Group

```shell
# With shell, you can just pass the correct header with each request
curl -X PUT -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
  -d '{
	"name": "Template Group 1",
	"templates": [
	{
	  "type": "IMAGE",
	  "singleSnapshotSecond": 12,
	  "snapshotIntervalSecond": 20,
	  "stripeIntervalSecond": 5,
	  "snapshotCount": 5,
	  "maxHeight": 320,
	  "maxWidth": 480,
	  "container": "h264"
	}
	],
	"useByDefault": false,
	"options": {
	"prefixAssetSid": "xqwe32a",
	"postfixAssetSid": "xqwe32q",
	"overlayImages": [
	  {
		"assetSid": "xcz243S",
		"location": "TOP_LEFT"
	  },
	  {
		"assetSid": "xcz243S",
		"location": "TOP_RIGHT"
	  }
	],
	"textLine1": {
	  "backgroundColor": null,
	  "backgroundImageAssetSid": "xcvxds21",
	  "opacity": "0.8",
	  "fontColor": "pink",
	  "text": "This should be seen on the video 111.",
	  "marquee": false
	},
	"textLine2": {
	  "backgroundColor": null,
	  "backgroundImageAssetSid": "xcvxds21",
	  "opacity": "0.8",
	  "fontColor": "pink",
	  "text": "This should be seen on the video 222.",
	  "marquee": false
	}
	}
  }' "https://api.nocvp.com/v1/template-group/54ec6ebbc757695a020041a8"
```

```http
PUT /v1/template-group/5572bd24c75769740a0041d6 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
  "name": "Template Group 1",
  "templates": [
	{
	  "type": "IMAGE",
	  "singleSnapshotSecond": 12,
	  "snapshotIntervalSecond": 20,
	  "stripeIntervalSecond": 5,
	  "snapshotCount": 5,
	  "maxHeight": 320,
	  "maxWidth": 480,
	  "container": "h264"
	}
  ],
  "useByDefault": false,
  "options": {
	"prefixAssetSid": "xqwe32a",
	"postfixAssetSid": "xqwe32q",
	"overlayImages": [
	  {
		"assetSid": "xcz243S",
		"location": "TOP_LEFT"
	  },
	  {
		"assetSid": "xcz243S",
		"location": "TOP_RIGHT"
	  }
	],
	"textLine1": {
	  "backgroundColor": null,
	  "backgroundImageAssetSid": "xcvxds21",
	  "opacity": "0.8",
	  "fontColor": "pink",
	  "text": "This should be seen on the video 111.",
	  "marquee": false
	},
	"textLine2": {
	  "backgroundColor": null,
	  "backgroundImageAssetSid": "xcvxds21",
	  "opacity": "0.8",
	  "fontColor": "pink",
	  "text": "This should be seen on the video 222.",
	  "marquee": false
	}
  }
}
```

> The above command returns JSON structured to <a href="/#list-template-group">Template Group Object</a>:

#### HTTP Request

`PUT https://api.nocvp.com/v1/template-group/:id`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>name</b> | string | template group title
useByDefault | boolean | use by default option
templates | array | <a href="/#video-transcoding-template-object-structure">videoConversionTemplate</a>, <a href="/#audio-transcoding-template-object-structure">audioConversionTemplate</a> or <a href="/#image-transcoding-template-object-structure">imageConversionTemplate</a> each one
options | object | <a href="/#template-group-options-structure">templateGroupOptionsObject</a>

#### Response Parameters

The Response likes <a href="/#list-template-group">Template Group Object</a>

## Delete Template Group

```shell
# With shell, you can just pass the correct header with each request
curl -X DELETE -H "Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d" "https://api.nocvp.com/v1/template-group/54ec6d59c757695b020041a9"
```

```http
DELETE /v1/template-group/54ec6d59c757695b020041a9 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d
```

> The above command returns JSON structured to <a href="/#list-template-group">Template Group Object</a>:

#### HTTP Request

`DELETE https://api.nocvp.com/v1/template-group/:id`

#### Response

The Response must be empty and http status code 204 No Content
