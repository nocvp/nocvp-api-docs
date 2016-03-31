# Assets

## List Assets

```shell
# With shell, you can just pass the correct header with each request
curl -X GET -H "Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6"
 "https://api.nocvp.com/v1/asset[/:id]/?queryStringParameters"
```

```http
GET /v1/asset[/:id]/?queryStringParameters HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6
```

> The above command returns JSON structured like this:

```json
[
  {
    "category": "56f3f2a800ddb373068b5174",
    "sid": "7Bd9g4yg",
    "creationTime": 1458827899404,
    "poster": {
      "type": "IMAGE",
      "sid": "7Bd9iomw",
      "id": "56f3f2a800ddb373068b5174",
      "height": 360,
      "width": 640,
      "size": 210606,
      "tags": [],
      "creationTime": 1458827944580,
      "status": null,
      "container": "jpg",
      "contentType": null
    },
    "jobs": [
      {
        "progress": 100,
        "template": {
          "type": "IMAGE",
          "maxHeight": 480,
          "maxWidth": 640,
          "creationTime": 1458742871986,
          "id": "56f2a65700ddb3e5358b502f",
          "container": "jpg"
        },
        "lastUpdatedTime": 1458827944552,
        "startTime": 1458827912226,
        "creationTime": 1458827909228,
        "id": "56f3f28500ddb372068b5167",
        "errorCode": null,
        "errorMessage": null,
        "state": "COMPLETE",
        "sid": "7Bd9gypt",
        "conversionId": "56f3f28500ddb372068b5166"
      },
      {
        "progress": 100,
        "template": {
          "type": "VIDEO",
          "audioBitrate": "128k",
          "audioChannels": 2,
          "audioCodec": "libfdk_aac",
          "audioSampleRate": 44100,
          "frameRate": "29.97",
          "videoBitrate": "1200k",
          "videoCodec": "libx264",
          "transmuxToHls": null,
          "bufferSize": null,
          "constantRatefactor": null,
          "fixedNumberOfFramesBetweenKeyframes": null,
          "maxBitRate": null,
          "maximumNumberOfFramesBetweenKeyframes": null,
          "rateControl": "targetBitrate",
          "videoMaxFrameRate": null,
          "maxHeight": 480,
          "maxWidth": 854,
          "creationTime": 1458742871993,
          "id": "56f2a65700ddb3e5358b5030",
          "container": "mp4"
        },
        "lastUpdatedTime": 1458828049861,
        "startTime": 1458827947661,
        "creationTime": 1458827909503,
        "id": "56f3f28500ddb372068b516d",
        "errorCode": null,
        "errorMessage": null,
        "state": "COMPLETE",
        "sid": "7Bd9gxLR",
        "conversionId": "56f3f28500ddb372068b516c"
      }
    ],
    "conversions": [
      {
        "type": "IMAGE",
        "sid": "7Bd9gypt",
        "id": "56f3f28500ddb372068b5166",
        "height": 360,
        "width": 640,
        "size": 210606,
        "tags": [],
        "creationTime": 1458742871986,
        "status": null,
        "container": "jpg",
        "contentType": null
      },
      {
        "type": "VIDEO",
        "sid": "7Bd9gxLR",
        "id": "56f3f28500ddb372068b516c",
        "audioBitrate": 128,
        "audioChannels": 2,
        "audioCodec": "libfdk_aac",
        "audioSampleRate": 44100,
        "duration": 287.578333,
        "frameRate": "29.97",
        "height": 480,
        "videoBitrate": 1200,
        "videoCodec": "libx264",
        "width": 854,
        "size": 45115895,
        "tags": [],
        "creationTime": 1458742871993,
        "status": null,
        "container": "mp4",
        "contentType": null
      }
    ],
    "author": null,
    "title": "Indila - S.O.S",
    "description": "« SOS », 3eme extrait de Mini World\nCompositeurs: Indila -- Skalpovich\nAuteur: Indila\nRéalisateur : Karim Ouaret\n\n« Mini World » sur iTunes : http://po.st/MiniWorld\nFacebook : https://www.facebook.com/IndilaOfficiel\nTwitter : https://twitter.com/Indila",
    "client": null,
    "id": "56f3f27b00ddb348078b5165",
    "source": {
      "type": "VIDEO",
      "sid": null,
      "id": "56f3f28500ddb372068b5165",
      "audioBitrate": 191999,
      "audioChannels": 0,
      "audioCodec": "aac",
      "audioSampleRate": null,
      "duration": 287.578333,
      "frameRate": "25",
      "height": 720,
      "videoBitrate": 1760925,
      "videoCodec": "h264",
      "width": 1280,
      "size": 70287590,
      "tags": [
        "und",
        "VideoHandler"
      ],
      "creationTime": 1458827909147,
      "status": "READY",
      "container": "mp4",
      "contentType": "video/mp4"
    },
    "tags": [],
    "user": {
      "id": "55546c1c00ddb386548b456f",
      "username": "adminuser"
    },
    "privacy": "PRIVATE",
    "published": null,
    "viewCounts": 3,
    "referenceId": null,
    "referenceUrl": "https://www.youtube.com/watch?v=m65jhGwtWrg",
    "deliveryStatus": "ACTIVE"
  }
]
```

#### HTTP Request

`GET /v1/asset[/:id]/?queryStringParameters`

#### Query String Parameters

Parameter | Type | Description
--------- | ------- | -----------
limit | integer | Limit of asset list. Min 1, Max 200
offset | integer | offset of asset list.
sourceStreamName | mixed | source stream name of live or live events
sourceType | enumerated (VIDEO,AUDIO,IMAGE,OTHER,LIVE,LIVE_EVENT) | source type of asset
sid | mixed | asset short id
category | array | asset category ids for example: &category[]=category1Id&category[]=category2Id
referenceId | mixed | your reference id
referenceIds | array | your reference ids of array for example: &referenceIds[]=your-ref1&referenceIds[]=your-ref2
title | mixed | asset title
tags | array | asset tags for example: &tags[]=tag1&tags[]=tag2
startTime | long (timestamp) | timestamp of milliseconds. list will be return creationTime >= startTime
endTime | long (timestamp) | timestamp of milliseconds. list will be return creationTime <= endTime
userId | mixed | your user id
q | mixed | any mixed text for full text search
sortBy | object | key allowed 1 or -1, 1 is ascending and -1 is descending sorting for example: &sortBy[title]=1&sortBy[creationTime]=-1

#### Response Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | mixed | you need the id while private asset embedding
sid | mixed | you need the short id while public or private asset embedding
title | mixed | asset title
description | mixed | asset description
tags | array | tag each one
author | mixed | author of asset
user | mixed | user reference id
client | mixed | api client reference id
category | mixed | category reference id
poster | <a href="#image-file-object-structure-extends-file-object-structure">imageFile</a> | Poster reference object
jobs | array | <a href="#transcoding-job-object-structure">transcodingJob</a> Object each one
conversions | array | <a href="#image-file-object-structure-extends-file-object-structure">imageFile</a> , <a href="#video-file-object-structure-extends-file-object-structure">videoFile</a> or <a href="#audio-file-object-structure-extends-file-object-structure">audioFile</a> object each one
source | object | <a href="#image-file-object-structure-extends-file-object-structure">imageFile</a> , <a href="#video-file-object-structure-extends-file-object-structure">videoFile</a>, <a href="#audio-file-object-structure-extends-file-object-structure">audioFile</a>, <a href="#live-source-object-structure">liveSource</a>, <a href="#live-event-source-object-structure">liveEventSource</a>, <a href="#live-pull-source-object-structure">livePullSource</a> object
privacy | enumerated | (PUBLIC or PRIVATE)
published | boolean | published status of live sources
viewCounts | long | view counts of asset
referenceId | mixed | your reference id
referenceUrl | mixed | your reference url youtube, daily motion, another ...etc
deliveryStatus | enumerated | (ACTIVE, PASSIVE or SUSPENDED)
creationTime | long | creation time of milliseconds

## Update Asset

```shell
# With shell, you can just pass the correct header with each request
curl -X PUT -H "Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d" -H "Content-Type: application/json" -H  -d '{
    "title": "New Title",
    "privacy": "PUBLIC|PRIVATE",
    "category": "5426422v4g4g2g34g43g34",
    "description": "New description",
    "tags": ["new tag1", "new tag2"],
    "author": "Copyright Noc INC"
}' "https://api.nocvp.com/v1/asset/7Bd9g4yg"
```

```http
PUT /v1/asset/7Bd9g4yg HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
    "title": "New Title",
    "privacy": "PUBLIC|PRIVATE",
    "category": "5426422v4g4g2g34g43g34",
    "description": "New description",
    "tags": ["new tag1", "new tag2"],
    "author": "Copyright Noc INC"
}
```

> The above command returns JSON structured to <a href="#list-assets">Asset Object</a>:

#### HTTP Request

`PUT https://api.nocvp.com/v1/asset/:id`

#### Query Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
title | mixed | asset title
privacy | enumerated | privacy (PUBLIC or PRIVATE)
category | mixed | category reference id
description | mixed | asset description
tags | array | asset tags
author | mixed | asset author

#### Response Parameters

The Response likes <a href="#list-assets">Asset Object</a>

## Delete Asset

```shell
# With shell, you can just pass the correct header with each request
curl -X DELETE -H "Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d" "https://api.nocvp.com/v1/asset/54ec6d59c757695b020041a9"
```

```http
DELETE /v1/asset/54ec6d59c757695b020041a9 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d
```

> The above command returns JSON structured to <a href="#list-assets">Asset Object</a>:

#### HTTP Request

`DELETE https://api.nocvp.com/v1/asset/:id`

#### Response

The Response must be empty and http status code 204 No Content


## Poster Upload

set to isPoster true and set asset reference id

You need to the <a href="#add-media">upload flow</a>
