# Playlist

## List Playlist

```shell
# With shell, you can just pass the correct header with each request
curl -X GET -H "Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6"
 "https://api.nocvp.com/v1/playlist[/:id]/?queryStringParameters"
```

```http
GET /v1/playlist[/:id]/?queryStringParameters HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6
```

> The above command returns JSON structured like this:

```json
[
  {
      "id": "558be4b3c75769c2090041a7",
      "sid": "7v1CRnVx",
      "title": "test 2",
      "type": "MATCHING_TAGS",
      "tags": [],
      "items": [],
      "privacy": "PUBLIC",
      "tagFilterType": null,
      "order": null,
      "limit": null,
      "creationTime": 1435231411702
  }
]
```

#### HTTP Request

`GET /v1/playlist[/:id]/?queryStringParameters`

#### Query String Parameters

Parameter | Type | Description
--------- | ------- | -----------
limit | integer | Limit of playlist list. Min 1, Max 200
offset | integer | offset of playlist list.

#### Response Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | string | playlist id
sid | string | playlist short id
title | string | playlist title
type | enumerated | (MATCHING_TAGS or MANUAL)
tags | array | asset tag each one
items | array | <a href="#playlist-item-object-structure">playlistItemObject</a> each one
privacy | enumerated | (PUBLIC or PRIVACY)
tagFilterType | enumerated | (ANY or ALL) any tag matching or all tags matching required
order | enumerated | (CREATION_DATE_DESC, CREATION_DATE_ASC, VIEWS_DESC, VIEWS_ASC)
limit | integer | Limit of playlist asset list. Min 1, Max 16
creationTime | long | creation time of milliseconds

## Create Playlist

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
    -d '{
        "title": "test",
        "privacy": "PUBLIC",
        "type": "MATCHING_TAGS",
        "tagFilterType": "ANY",
        "tags": ["tag1", "tag2"],
        "limit": "10",
        "order": "CREATION_DATE_DESC"
    }' "https://api.nocvp.com/v1/playlist"
```

```http
POST /v1/playlist HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
	"title": "test",
	"privacy": "PUBLIC",
	"type": "MATCHING_TAGS",
	"tagFilterType": "ANY",
	"tags": ["tag1", "tag2"],
	"limit": "10",
	"order": "CREATION_DATE_DESC"
}
```

> The above command returns JSON structured to <a href="#list-playlist">Playlist Object</a>:

#### HTTP Request

`POST https://api.nocvp.com/v1/playlist`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>title</b> | string | playlist title
<b>type</b> | enumerated | (MATCHING_TAGS or MANUAL)
tags | array | required if type is MATCHING_TAGS
items | array | required if type is MANUAL, must object and keys must be assetId and sort each one
privacy | enumerated | (PUBLIC or PRIVACY)
tagFilterType | enumerated |  required if type is MATCHING_TAGS (ANY or ALL) any tag matching or all tags matching required
order | enumerated | (CREATION_DATE_DESC, CREATION_DATE_ASC, VIEWS_DESC, VIEWS_ASC)
limit | integer | Limit of playlist asset list. Min 1, Max 16

#### Response Parameters

The Response likes <a href="#list-playlist">Playlist Object</a>


## Update Playlist

```shell
# With shell, you can just pass the correct header with each request
curl -X PUT -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
    -d '{
		"title": "test",
		"privacy": "PUBLIC",
		"type": "MATCHING_TAGS",
		"tagFilterType": "ANY",
		"tags": ["tag1", "tag2"],
		"limit": "10",
		"order": "CREATION_DATE_DESC"
	}' "https://api.nocvp.com/v1/playlist/54ec6ebbc757695a020041a8"
```

```http
PUT /v1/playlist/5572bd24c75769740a0041d6 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
	"title": "test",
	"privacy": "PUBLIC",
	"type": "MATCHING_TAGS",
	"tagFilterType": "ANY",
	"tags": ["tag1", "tag2"],
	"limit": "10",
	"order": "CREATION_DATE_DESC"
}
```

> The above command returns JSON structured to <a href="#list-playlist">Playlist Object</a>:

#### HTTP Request

`PUT https://api.nocvp.com/v1/playlist/:id`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>title</b> | string | playlist title
<b>type</b> | enumerated | (MATCHING_TAGS or MANUAL)
tags | array | required if type is MATCHING_TAGS
items | array | required if type is MANUAL, must object and keys must be assetId and sort each one
privacy | enumerated | (PUBLIC or PRIVACY)
tagFilterType | enumerated |  required if type is MATCHING_TAGS (ANY or ALL) any tag matching or all tags matching required
order | enumerated | (CREATION_DATE_DESC, CREATION_DATE_ASC, VIEWS_DESC, VIEWS_ASC)
limit | integer | Limit of playlist asset list. Min 1, Max 16

#### Response Parameters

The Response likes <a href="#list-playlist">Playlist Object</a>

## Delete Playlist

```shell
# With shell, you can just pass the correct header with each request
curl -X DELETE -H "Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d" "https://api.nocvp.com/v1/playlist/54ec6d59c757695b020041a9"
```

```http
DELETE /v1/playlist/54ec6d59c757695b020041a9 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d
```

> The above command returns JSON structured to <a href="#list-playlist">Playlist Object</a>:

#### HTTP Request

`DELETE https://api.nocvp.com/v1/playlist/:id`

#### Response

The Response must be empty and http status code 204 No Content
