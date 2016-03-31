# Advertising

## List Advertising

```shell
# With shell, you can just pass the correct header with each request
curl -X GET -H "Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6"
 "https://api.nocvp.com/v1/advertising[/:id]/?queryStringParameters"
```

```http
GET /v1/advertising[/:id]/?queryStringParameters HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6
```

> The above command returns JSON structured like this:

```json
[
  {
      "id": "56e19ac586ec356dc20041ac",
      "sid": "7ATQ1ajS",
      "title": "Ads 1",
      "type": "URI",
      "adTagUri": [],
      "adBreaks": [
        {
          "breakType": [
            "LINEAR"
          ],
          "timeOffset": "124325",
          "allowMultipleAds": false,
          "followRedirects": false,
          "adTagUri": [
            {
              "weight": 90,
              "uri": "https://googleads.g.doubleclick.net/pagead/ads?...xml_vast3"
            }
          ]
        }
      ],
      "creationTime": 1457625797536
  }
]
```

#### HTTP Request

`GET /v1/advertising[/:id]/?queryStringParameters`

#### Query String Parameters

Parameter | Type | Description
--------- | ------- | -----------
limit | integer | Limit of advertising list. Min 1, Max 200
offset | integer | offset of advertising list.

#### Response Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | string | ads id
sid | string | ads short id
title | string | ads title
type | enumerated | (URI or CUSTOM)
adTagUri | array | <a href="/#player-ads-ad-tag-uri-object-structure">adTagUriObject</a> each one
adBreaks | array | <a href="/#player-ads-ad-break-object-structure">adBreakObject</a> each one
creationTime | long | creation time of milliseconds

## Create Advertising

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
-d '{
	  "title": "Ads 1",
	  "type": "URI",
	  "adTagUri": [],
	  "adBreaks": [
		{
		  "breakType": [
			"LINEAR"
		  ],
		  "timeOffset": "124325",
		  "allowMultipleAds": false,
		  "followRedirects": false,
		  "adTagUri": [
			{
			  "weight": 90,
			  "uri": "https://googleads.g.doubleclick.net/pagead/ads?...xml_vast3"
			}
		  ]
		}
	  ]
  }' "https://api.nocvp.com/v1/advertising"
```

```http
POST /v1/advertising HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
  "title": "Ads 1",
  "type": "URI",
  "adTagUri": [],
  "adBreaks": [
    {
      "breakType": [
        "LINEAR"
      ],
      "timeOffset": "124325",
      "allowMultipleAds": false,
      "followRedirects": false,
      "adTagUri": [
        {
          "weight": 90,
          "uri": "https://googleads.g.doubleclick.net/pagead/ads?...xml_vast3"
        }
      ]
    }
  ]
}
```

> The above command returns JSON structured to <a href="/#list-advertising">Advertising Object</a>:

#### HTTP Request

`POST https://api.nocvp.com/v1/advertising`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>title</b> | string | ads title
type | enumerated | (URI or CUSTOM)
adTagUri | array | <a href="/#player-ads-ad-tag-uri-object-structure">adTagUriObject</a> each one
adBreaks | array | <a href="/#player-ads-ad-break-object-structure">adBreakObject</a> each one

#### Response Parameters

The Response likes <a href="/#list-advertising">Advertising Object</a>


## Update Advertising

```shell
# With shell, you can just pass the correct header with each request
curl -X PUT -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
    -d '{
      "title": "Ads 1",
      "type": "URI",
      "adTagUri": [],
      "adBreaks": [
        {
          "breakType": [
            "LINEAR"
          ],
          "timeOffset": "124325",
          "allowMultipleAds": false,
          "followRedirects": false,
          "adTagUri": [
            {
              "weight": 90,
              "uri": "https://googleads.g.doubleclick.net/pagead/ads?...xml_vast3"
            }
          ]
        }
      ]
    }' "https://api.nocvp.com/v1/advertising/54ec6ebbc757695a020041a8"
```

```http
PUT /v1/advertising/5572bd24c75769740a0041d6 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
  "title": "Ads 1",
  "type": "URI",
  "adTagUri": [],
  "adBreaks": [
    {
      "breakType": [
        "LINEAR"
      ],
      "timeOffset": "124325",
      "allowMultipleAds": false,
      "followRedirects": false,
      "adTagUri": [
        {
          "weight": 90,
          "uri": "https://googleads.g.doubleclick.net/pagead/ads?...xml_vast3"
        }
      ]
    }
  ]
}
```

> The above command returns JSON structured to <a href="/#list-advertising">Advertising Object</a>:

#### HTTP Request

`PUT https://api.nocvp.com/v1/advertising/:id`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>title</b> | string | ads title
type | enumerated | (URI or CUSTOM)
adTagUri | array | <a href="/#player-ads-ad-tag-uri-object-structure">adTagUriObject</a> each one
adBreaks | array | <a href="/#player-ads-ad-break-object-structure">adBreakObject</a> each one

#### Response Parameters

The Response likes <a href="/#list-advertising">Advertising Object</a>

## Delete Advertising

```shell
# With shell, you can just pass the correct header with each request
curl -X DELETE -H "Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d" "https://api.nocvp.com/v1/advertising/54ec6d59c757695b020041a9"
```

```http
DELETE /v1/advertising/54ec6d59c757695b020041a9 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d
```

> The above command returns JSON structured to <a href="/#list-advertising">Advertising Object</a>:

#### HTTP Request

`DELETE https://api.nocvp.com/v1/advertising/:id`

#### Response

The Response must be empty and http status code 204 No Content
