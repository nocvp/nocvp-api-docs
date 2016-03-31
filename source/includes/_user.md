# User

## List User

```shell
# With shell, you can just pass the correct header with each request
curl -X GET -H "Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6"
 "https://api.nocvp.com/v1/user[/:id]/?queryStringParameters"
```

```http
GET /v1/user[/:id]/?queryStringParameters HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6
```

> The above command returns JSON structured like this:

```json
[
  {
      "id": "5572bd22c75769740a0041b0",
      "firstName": "First",
      "lastName": "Last",
      "username": "john_doe",
      "email": "john_doe@noc.com.tr",
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

`GET /v1/user[/:id]/?queryStringParameters`

#### Query String Parameters

Parameter | Type | Description
--------- | ------- | -----------
limit | integer | Limit of user list. Min 1, Max 200
offset | integer | offset of user list.

#### Response Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | string | user id
firstName | string | user first name
lastName | string | user last name
username | string | user name for login must be alphanumeric
password | string | password for login must be alphanumeric
email | string | user contact email address
privileges | array | (account_summary, asset, transcoding_job, poster, conversion, player, playlist, playout, user, client, upload, upload_from_url, template_group, profile, category, live, analytics, advertising) privileges each one
creationTime | long | creation time of milliseconds

## Create User

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
  -d '{
  		"firstName": "First",
  		"lastName": "Last",
  		"username": "john_doe",
  		"email": "john_doe@noc.com.tr",
  		"password": "john-1245",
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
  	}' "https://api.nocvp.com/v1/user/12345ebbc757695a02012345"
```

```http
POST /v1/user HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
	"firstName": "First",
	"lastName": "Last",
	"username": "john_doe",
	"email": "john_doe@noc.com.tr",
	"password": "john-1245",
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

> The above command returns JSON structured to <a href="#list-user">User Object</a>:

#### HTTP Request

`POST https://api.nocvp.com/v1/user`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>firstName</b> | string | user first name
<b>lastName</b> | string | user last name
<b>username</b> | string | user name for login must be alphanumeric
<b>password</b> | string | password for login must be alphanumeric
<b>email</b> | string | user contact email address
<b>privileges</b> | array | (account_summary, asset, transcoding_job, poster, conversion, player, playlist, playout, user, client, upload, upload_from_url, template_group, profile, category, live, analytics, advertising) privileges each one

#### Response Parameters

The Response likes <a href="#list-user">User Object</a>


## Update User

```shell
# With shell, you can just pass the correct header with each request
curl -X PUT -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
    -d '{
		"firstName": "First",
		"lastName": "Last",
		"username": "john_doe",
		"email": "john_doe@noc.com.tr",
		"password": "john-1245",
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
	}' "https://api.nocvp.com/v1/user/12345ebbc757695a02012345"
```

```http
PUT /v1/user/5572bd24c75769740a0041d6 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
	"firstName": "First",
	"lastName": "Last",
	"username": "john_doe",
	"email": "john_doe@noc.com.tr",
	"password": "john-1245",
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

> The above command returns JSON structured to <a href="#list-user">User Object</a>:

#### HTTP Request

`PUT https://api.nocvp.com/v1/user/:id`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>firstName</b> | string | user first name
<b>lastName</b> | string | user last name
<b>username</b> | string | user name for login must be alphanumeric
<b>password</b> | string | password for login must be alphanumeric
<b>email</b> | string | user contact email address
<b>privileges</b> | array | (account_summary, asset, transcoding_job, poster, conversion, player, playlist, playout, user, client, upload, upload_from_url, template_group, profile, category, live, analytics, advertising) privileges each one

#### Response Parameters

The Response likes <a href="#list-user">User Object</a>

## Delete User

```shell
# With shell, you can just pass the correct header with each request
curl -X DELETE -H "Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d" "https://api.nocvp.com/v1/user/54ec6d59c757695b020041a9"
```

```http
DELETE /v1/user/54ec6d59c757695b020041a9 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d
```

> The above command returns JSON structured to <a href="#list-user">User Object</a>:

#### HTTP Request

`DELETE https://api.nocvp.com/v1/user/:id`

#### Response

The Response must be empty and http status code 204 No Content
