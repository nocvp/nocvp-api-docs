# Category

## List Category

```shell
# With shell, you can just pass the correct header with each request
curl -X GET -H "Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6"
 "https://api.nocvp.com/v1/category[/:id]/?queryStringParameters"
```

```http
GET /v1/category[/:id]/?queryStringParameters HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6
```

> The above command returns JSON structured like this:

```json
[
  { 
      "id" : "111e89f3d672480461234567", 
      "title" : "Rock Video Clips", 
      "sid" : "7txh7123", 
      "poster" : {
          "id" : "111763dbd67248396f8b1234", 
          "sid" : "7tyg6123", 
          "container" : "jpeg", 
          "size" : 47524, 
          "width" : 1040, 
          "height" : 370, 
          "creation_time" : 1429693403131
      },
      "creation_time" : 1429113331523
  }
]
```

#### HTTP Request

`GET /v1/category[/:id]/?queryStringParameters`

#### Query String Parameters

Parameter | Type | Description
--------- | ------- | -----------
limit | integer | Limit of category list. Min 1, Max 200
offset | integer | offset of category list.

#### Response Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | string | category id
sid | string | category short id
title | string | category title
poster | object | <a href="#image-file-object-structure-extends-file-object-structure">imageFileObject</a>
creationTime | long | creation time of milliseconds

## Create Category

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
-d '{ 
	  "title" : "Rock Video Clips"
  }' "https://api.nocvp.com/v1/category"
```

```http
POST /v1/category HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{ 
  "title" : "Rock Video Clips"
}
```

> The above command returns JSON structured to <a href="#list-category">Category Object</a>:

#### HTTP Request

`POST https://api.nocvp.com/v1/category`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>title</b> | string | category title

#### Response Parameters

The Response likes <a href="#list-category">Category Object</a>


## Update Category

```shell
# With shell, you can just pass the correct header with each request
curl -X PUT -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
	-d '{ 
		  "title" : "Rock Video Clips"
	  }' "https://api.nocvp.com/v1/category/54ec6ebbc757695a020041a8"
```

```http
PUT /v1/category/5572bd24c75769740a0041d6 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{ 
  "title" : "Rock Video Clips"
}
```

> The above command returns JSON structured to <a href="#list-category">Category Object</a>:

#### HTTP Request

`PUT https://api.nocvp.com/v1/category/:id`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>title</b> | string | category title

#### Response Parameters

The Response likes <a href="#list-category">Category Object</a>

## Delete Category

```shell
# With shell, you can just pass the correct header with each request
curl -X DELETE -H "Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d" "https://api.nocvp.com/v1/category/54ec6d59c757695b020041a9"
```

```http
DELETE /v1/category/54ec6d59c757695b020041a9 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d
```

> The above command returns JSON structured to <a href="#list-category">Category Object</a>:

#### HTTP Request

`DELETE https://api.nocvp.com/v1/category/:id`

#### Response

The Response likes <a href="#list-category">Category Object</a> with additional fields of deletedAt and deletedBy.

## Poster Upload

Poster upload process is almost same with add media flow, only difference is setting isPoster to true and asset or category fields.

Have a look to <a href="#add-media">add media flow.</a>