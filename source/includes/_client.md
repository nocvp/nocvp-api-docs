# Client

## List Client

```shell
# With shell, you can just pass the correct header with each request
curl -X GET -H "Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6"
 "https://api.nocvp.com/v1/client[/:id]/?queryStringParameters"
```

```http
GET /v1/client[/:id]/?queryStringParameters HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6
```

> The above command returns JSON structured like this:

```json
[
  {
      "id": "5572bd22c75769740a0041b0",
      "clientSecretOriginal": "3523f23f32f23ff32f324242",
	  "clientId": "3523f23f32f23ff32f241442",
	  "grantTypes": "client_credentials",
      "privileges": [
        "asset",
        "transcoding_job",
        "conversion",
        "playlist",
        "playout",
        "upload",
        "profile",
        "category",
        "template_group",
        "player",
        "account_summary"
      ],
      "creationTime": 1433582883000
  }
]
```

#### HTTP Request

`GET /v1/client[/:id]/?queryStringParameters`

#### Query String Parameters

Parameter | Type | Description
--------- | ------- | -----------
limit | integer | Limit of client list. Min 1, Max 200
offset | integer | offset of client list.

#### Response Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | string | client reference id
clientId | string | client id for access
clientSecretOriginal | string | client secret for access
grantTypes | enumerated | only accessible <b>client_credentials</b> type
privileges | array | (account_summary, asset, transcoding_job, poster, conversion, player, playlist, playout, user, client, upload, upload_from_url, template_group, profile, category, live, analytics, advertising) privileges each one
creationTime | long | creation time of milliseconds

## Create Client

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
  -d '{
	    "grantTypes": "client_credentials",
  		"privileges": [
			"asset",
			"transcoding_job",
			"conversion",
			"playlist",
			"playout",
			"upload",
			"profile",
			"category",
			"template_group",
			"player",
			"account_summary"
  		]
  	}' "https://api.nocvp.com/v1/client/12345ebbc757695a02012345"
```

```http
POST /v1/client HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
	"grantTypes": "client_credentials",
	"privileges": [
		"asset",
		"transcoding_job",
		"conversion",
		"playlist",
		"playout",
		"upload",
		"profile",
		"category",
		"template_group",
		"player",
		"account_summary"
	]
}
```

> The above command returns JSON structured to <a href="#list-client">Client Object</a>:

#### HTTP Request

`POST https://api.nocvp.com/v1/client`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>grantTypes</b> | enumerated | only accessible <b>client_credentials</b> type
<b>privileges</b> | array | (account_summary, asset, transcoding_job, poster, conversion, player, playlist, playout, user, client, upload, upload_from_url, template_group, profile, category, live, analytics, advertising) privileges each one

#### Response Parameters

The Response likes <a href="#list-client">Client Object</a>


## Update Client

```shell
# With shell, you can just pass the correct header with each request
curl -X PUT -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
    -d '{
		"grantTypes": "client_credentials",
		"privileges": [
			"asset",
			"transcoding_job",
			"conversion",
			"playlist",
			"playout",
			"upload",
			"profile",
			"category",
			"template_group",
			"player",
			"account_summary"
		]
	}' "https://api.nocvp.com/v1/client/12345ebbc757695a02012345"
```

```http
PUT /v1/client/5572bd24c75769740a0041d6 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
	"grantTypes": "client_credentials",
	"privileges": [
		"asset",
		"transcoding_job",
		"conversion",
		"playlist",
		"playout",
		"upload",
		"profile",
		"category",
		"template_group",
		"player",
		"account_summary"
	]
}
```

> The above command returns JSON structured to <a href="#list-client">Client Object</a>:

#### HTTP Request

`PUT https://api.nocvp.com/v1/client/:id`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>grantTypes</b> | enumerated | only accessible <b>client_credentials</b> type
<b>privileges</b> | array | (account_summary, asset, transcoding_job, poster, conversion, player, playlist, playout, user, client, upload, upload_from_url, template_group, profile, category, live, analytics, advertising) privileges each one

#### Response Parameters

The Response likes <a href="#list-client">Client Object</a>

## Delete Client

```shell
# With shell, you can just pass the correct header with each request
curl -X DELETE -H "Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d" "https://api.nocvp.com/v1/client/54ec6d59c757695b020041a9"
```

```http
DELETE /v1/client/54ec6d59c757695b020041a9 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d
```

> The above command returns JSON structured to <a href="#list-client">Client Object</a>:

#### HTTP Request

`DELETE https://api.nocvp.com/v1/client/:id`

#### Response

The Response must be empty and http status code 204 No Content
