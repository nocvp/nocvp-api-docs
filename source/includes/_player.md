# Players

## List Players

```shell
# With shell, you can just pass the correct header with each request
curl -X GET -H "Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6"
 "https://api.nocvp.com/v1/player[/:id]/?queryStringParameters"
```

```http
GET /v1/player[/:id]/?queryStringParameters HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 6b66868c72c570dc78a44bc1f9c7e229485434b6
```

> The above command returns JSON structured like this:

```json
[
  {
    "sid": "7wx3gTcy",
    "creationTime": 1441033857738,
    "id": "55e46e8100ddb341788b5193",
    "autoPlay": true,
    "bgColor": "rgba(98,151,181,0.8)",
    "fullScreen": true,
    "iconColor": "#ffffff",
    "logo": "",
    "logoPosition": "LEFT_TOP",
    "name": "ads test",
    "playBar": true,
    "playButton": true,
    "progressColor": "#ffffff",
    "skin": "skin3",
    "socialButtons": {
      "scalar": false,
      "facebook": true,
      "twitter": true,
      "google": true,
      "pinterest": true,
      "linkedIn": true
    },
    "timeBar": true,
    "volumeControl": true,
    "controls": true,
    "muteButton": null,
    "timeRemaining": false,
    "privacy": "PUBLIC",
    "ads": {
      "id": "56e1cd6300ddb31a5c8b4674",
      "sid": "7AU2sjb9",
      "account": {},
      "title": "IMA Test",
      "type": "URI",
      "adTagUri": [
        {
          "weight": 100,
          "uri": "https://googleads.g.doubleclick.net/pagead/ads?client=ca-video-pub-8718605733307345&slotname=7827815991&ad_type=video_text_image_flash&description_url=http%3A%2F%2Ftv.haberler.com&videoad_start_delay=0&output=xml_vast3"
        }
      ],
      "adBreaks": [],
      "creationTime": 1457638755757
    },
    "googleAnalytics": "UA-11142111-11",
    "googleAnalyticsEvents": {
      "loaded": true,
      "percentsPlayed": true,
      "start": true,
      "end": true,
      "seek": true,
      "play": true,
      "pause": true,
      "resize": true,
      "volumeChange": true,
      "error": true,
      "fullscreen": true
    },
    "techs": [
      "html5",
      "hls",
      "flash"
    ],
    "playlistAutoPlayNext": true,
    "playlistRepeat": true,
    "playlistShuffle": true,
    "fontSize": 9,
    "endScreen": "RELATED",
    "endScreenContent": null
  }
]
```

#### HTTP Request

`GET /v1/player[/:id]/?queryStringParameters`

#### Query String Parameters

Parameter | Type | Description
--------- | ------- | -----------
limit | integer | Limit of player list. Min 1, Max 200
offset | integer | offset of player list.
sid | string | player short id

#### Response Parameters

Parameter | Type | Description
--------- | ------- | -----------
id | string | player id
sid | string | player sid
name | string | player title
playButton | boolean | show play button status
muteButton | boolean | show mute button status
playBar | boolean | show play bar status
volumeControl | boolean | show volume control status
fullScreen | boolean | show full screen button status
autoPlay | boolean | auto play status
controls | boolean | show control buttons status
timeBar | boolean | show time bar status
socialButtons | object | <a href="/#social-buttons-object-structure">socialButtonsObject</a>
timeRemaining | boolean | show time remaining status
iconColor | string | for example "#FFDDAA" or "rgba(98,151,181,0.8)"
progressColor | string | for example "#FFDDAA" or "rgba(98,151,181,0.8)"
bgColor | string | for example "#FFDDAA" or "rgba(98,151,181,0.8)"
skin | enumerated | (skin1, skin2, skin3)
logo | string | image asset reference sid 
fontSize | integer | font size pixel
logoPosition | enumerated | (TOP_LEFT, TOP_RIGHT, BOTTOM_LEFT, BOTTOM_RIGHT) 
privacy | enumerated | (PUBLIC or PRIVATE)
ads | object | <a href="/#player-ads-object-structure">adsObject</a>
googleAnalytics | string | google analytics id
googleAnalyticsEvents | object | <a href="/#player-google-analytics-object-structure">googleAnalyticsObject</a>
techs | array | (html5, hls, flash) strings each one 
playlistAutoPlayNext | boolean | auto play next video on playlist
playlistRepeat | boolean | auto repeat playlist
playlistShuffle | boolean | playlist shuffle
endScreen | enumerated | (DISABLED, RELATED, SOCIAL, CUSTOM) 
endScreenContent | string | video end screen content
creationTime | long | creation time of milliseconds

## Create Player

```shell
# With shell, you can just pass the correct header with each request
curl -X POST -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" 
-d '{
    "autoPlay": true,
    "bgColor": "rgba(98,151,181,0.8)",
    "fullScreen": true,
    "iconColor": "#ffffff",
    "logo": "6542gf943",
    "logoPosition": "LEFT_TOP",
    "name": "Test Player 1",
    "playBar": true,
    "playButton": true,
    "progressColor": "#ffffff",
    "skin": "skin3",
    "socialButtons": {
      "scalar": false,
      "facebook": true,
      "twitter": true,
      "google": true,
      "pinterest": true,
      "linkedIn": true
    },
    "timeBar": true,
    "volumeControl": true,
    "controls": true,
    "muteButton": null,
    "timeRemaining": false,
    "privacy": "PUBLIC",
    "ads": "5572bd24c75769740a0041d6",
    "googleAnalytics": "UA-11142111-11",
    "googleAnalyticsEvents": {
      "loaded": true,
      "percentsPlayed": true,
      "start": true,
      "end": true,
      "seek": true,
      "play": true,
      "pause": true,
      "resize": true,
      "volumeChange": true,
      "error": true,
      "fullscreen": true
    },
    "techs": [
      "html5",
      "hls",
      "flash"
    ],
    "playlistAutoPlayNext": true,
    "playlistRepeat": true,
    "playlistShuffle": true,
    "fontSize": 9,
    "endScreen": "RELATED",
    "endScreenContent": "end screen text here"
}' "https://api.nocvp.com/v1/player"
```

```http
POST /v1/player HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
    "autoPlay": true,
    "bgColor": "rgba(98,151,181,0.8)",
    "fullScreen": true,
    "iconColor": "#ffffff",
    "logo": "6542gf943",
    "logoPosition": "LEFT_TOP",
    "name": "Test Player 1",
    "playBar": true,
    "playButton": true,
    "progressColor": "#ffffff",
    "skin": "skin3",
    "socialButtons": {
      "scalar": false,
      "facebook": true,
      "twitter": true,
      "google": true,
      "pinterest": true,
      "linkedIn": true
    },
    "timeBar": true,
    "volumeControl": true,
    "controls": true,
    "muteButton": null,
    "timeRemaining": false,
    "privacy": "PUBLIC",
    "ads": "5572bd24c75769740a0041d6",
    "googleAnalytics": "UA-11142111-11",
    "googleAnalyticsEvents": {
      "loaded": true,
      "percentsPlayed": true,
      "start": true,
      "end": true,
      "seek": true,
      "play": true,
      "pause": true,
      "resize": true,
      "volumeChange": true,
      "error": true,
      "fullscreen": true
    },
    "techs": [
      "html5",
      "hls",
      "flash"
    ],
    "playlistAutoPlayNext": true,
    "playlistRepeat": true,
    "playlistShuffle": true,
    "fontSize": 9,
    "endScreen": "RELATED",
    "endScreenContent": "end screen text here"
}
```

> The above command returns JSON structured to <a href="/#list-players">Player Object</a>:

#### HTTP Request

`POST https://api.nocvp.com/v1/player`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>name</b> | string | player title
playButton | boolean | show play button status
muteButton | boolean | show mute button status
playBar | boolean | show play bar status
volumeControl | boolean | show volume control status
fullScreen | boolean | show full screen button status
autoPlay | boolean | auto play status
controls | boolean | show control buttons status
timeBar | boolean | show time bar status
socialButtons | object | <a href="/#social-buttons-object-structure">socialButtonsObject</a>
timeRemaining | boolean | show time remaining status
iconColor | string | for example "#FFDDAA" or "rgba(98,151,181,0.8)"
progressColor | string | for example "#FFDDAA" or "rgba(98,151,181,0.8)"
bgColor | string | for example "#FFDDAA" or "rgba(98,151,181,0.8)"
skin | enumerated | (skin1, skin2, skin3)
logo | string | image asset reference sid 
fontSize | integer | font size pixel
logoPosition | enumerated | (TOP_LEFT, TOP_RIGHT, BOTTOM_LEFT, BOTTOM_RIGHT) 
privacy | enumerated | (PUBLIC or PRIVATE)
ads | object | Advertising reference id
googleAnalytics | string | google analytics id
googleAnalyticsEvents | object | <a href="/#player-google-analytics-object-structure">googleAnalyticsObject</a>
techs | array | (html5, hls, flash) strings each one 
playlistAutoPlayNext | boolean | auto play next video on playlist
playlistRepeat | boolean | auto repeat playlist
playlistShuffle | boolean | playlist shuffle
endScreen | enumerated | (DISABLED, RELATED, SOCIAL, CUSTOM) 
endScreenContent | string | video end screen content

#### Response Parameters

The Response likes <a href="/#list-players">Player Object</a>


## Update Player

```shell
# With shell, you can just pass the correct header with each request
curl -X PUT -H "Authorization: Bearer 24237266067dac7f36ad1f3bd21421d55feb9561" -H "Content-Type: application/json" -d '{
    "autoPlay": true,
    "bgColor": "rgba(98,151,181,0.8)",
    "fullScreen": true,
    "iconColor": "#ffffff",
    "logo": "6542gf943",
    "logoPosition": "LEFT_TOP",
    "name": "Test Player 1",
    "playBar": true,
    "playButton": true,
    "progressColor": "#ffffff",
    "skin": "skin3",
    "socialButtons": {
      "scalar": false,
      "facebook": true,
      "twitter": true,
      "google": true,
      "pinterest": true,
      "linkedIn": true
    },
    "timeBar": true,
    "volumeControl": true,
    "controls": true,
    "muteButton": null,
    "timeRemaining": false,
    "privacy": "PUBLIC",
    "ads": "5572bd24c75769740a0041d6",
    "googleAnalytics": "UA-11142111-11",
    "googleAnalyticsEvents": {
      "loaded": true,
      "percentsPlayed": true,
      "start": true,
      "end": true,
      "seek": true,
      "play": true,
      "pause": true,
      "resize": true,
      "volumeChange": true,
      "error": true,
      "fullscreen": true
    },
    "techs": [
      "html5",
      "hls",
      "flash"
    ],
    "playlistAutoPlayNext": true,
    "playlistRepeat": true,
    "playlistShuffle": true,
    "fontSize": 9,
    "endScreen": "RELATED",
    "endScreenContent": "end screen text here"
}' "https://api.nocvp.com/v1/player/54ec6ebbc757695a020041a8"
```

```http
PUT /v1/player/5572bd24c75769740a0041d6 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer 5000ad6318dddf768e9689e6f909e85d334e835d
Content-Type: application/json

{
    "autoPlay": true,
    "bgColor": "rgba(98,151,181,0.8)",
    "fullScreen": true,
    "iconColor": "#ffffff",
    "logo": "6542gf943",
    "logoPosition": "LEFT_TOP",
    "name": "Test Player 1",
    "playBar": true,
    "playButton": true,
    "progressColor": "#ffffff",
    "skin": "skin3",
    "socialButtons": {
      "scalar": false,
      "facebook": true,
      "twitter": true,
      "google": true,
      "pinterest": true,
      "linkedIn": true
    },
    "timeBar": true,
    "volumeControl": true,
    "controls": true,
    "muteButton": null,
    "timeRemaining": false,
    "privacy": "PUBLIC",
    "ads": "5572bd24c75769740a0041d6",
    "googleAnalytics": "UA-11142111-11",
    "googleAnalyticsEvents": {
      "loaded": true,
      "percentsPlayed": true,
      "start": true,
      "end": true,
      "seek": true,
      "play": true,
      "pause": true,
      "resize": true,
      "volumeChange": true,
      "error": true,
      "fullscreen": true
    },
    "techs": [
      "html5",
      "hls",
      "flash"
    ],
    "playlistAutoPlayNext": true,
    "playlistRepeat": true,
    "playlistShuffle": true,
    "fontSize": 9,
    "endScreen": "RELATED",
    "endScreenContent": "end screen text here"
}
```

> The above command returns JSON structured to <a href="/#list-players">Player Object</a>:

#### HTTP Request

`PUT https://api.nocvp.com/v1/player/:id`

#### Request Parameters

`Elements in bold are mandatory. Default value is shown after equals sign.`

Parameter | Type | Description
--------- | ------- | -----------
<b>name</b> | string | player title
playButton | boolean | show play button status
muteButton | boolean | show mute button status
playBar | boolean | show play bar status
volumeControl | boolean | show volume control status
fullScreen | boolean | show full screen button status
autoPlay | boolean | auto play status
controls | boolean | show control buttons status
timeBar | boolean | show time bar status
socialButtons | object | <a href="/#social-buttons-object-structure">socialButtonsObject</a>
timeRemaining | boolean | show time remaining status
iconColor | string | for example "#FFDDAA" or "rgba(98,151,181,0.8)"
progressColor | string | for example "#FFDDAA" or "rgba(98,151,181,0.8)"
bgColor | string | for example "#FFDDAA" or "rgba(98,151,181,0.8)"
skin | enumerated | (skin1, skin2, skin3)
logo | string | image asset reference sid 
fontSize | integer | font size pixel
logoPosition | enumerated | (TOP_LEFT, TOP_RIGHT, BOTTOM_LEFT, BOTTOM_RIGHT) 
privacy | enumerated | (PUBLIC or PRIVATE)
ads | object | Advertising reference id
googleAnalytics | string | google analytics id
googleAnalyticsEvents | object | <a href="/#player-google-analytics-object-structure">googleAnalyticsObject</a>
techs | array | (html5, hls, flash) strings each one 
playlistAutoPlayNext | boolean | auto play next video on playlist
playlistRepeat | boolean | auto repeat playlist
playlistShuffle | boolean | playlist shuffle
endScreen | enumerated | (DISABLED, RELATED, SOCIAL, CUSTOM) 
endScreenContent | string | video end screen content

#### Response Parameters

The Response likes <a href="/#list-players">Player Object</a>

## Delete Player

```shell
# With shell, you can just pass the correct header with each request
curl -X DELETE -H "Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d" "https://api.nocvp.com/v1/player/54ec6d59c757695b020041a9"
```

```http
DELETE /v1/player/54ec6d59c757695b020041a9 HTTP/1.1
Host: api.nocvp.com
Authorization: Bearer da7377d7bb94a7651470d01b663be032b0dab51d
```

> The above command returns JSON structured to <a href="/#list-players">Player Object</a>:

#### HTTP Request

`DELETE https://api.nocvp.com/v1/player/:id`

#### Response

The Response must be empty and http status code 204 No Content
