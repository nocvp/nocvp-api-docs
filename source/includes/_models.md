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

Parameter | Type | Description
--------- | ------- | -----------
prefixAssetSid | string | asset sid for prefix
postfixAssetSid | string | asset sid for postfix
overlayImages[].assetSid | string | image asset sid
overlayImages[].location | enum | TOP_LEFT,TOP_RIGHT,BOTTOM_LEFT,BOTTOM_RIGHT
textLine1.backgroundColor | string | color code
textLine1.backgroundImageAssetSid | string | image asset sid
textLine1.opacity | float | text opacity between 0.1 - 1
textLine1.fontColor | string | color code
textLine1.text | string | your text here
textLine2.backgroundColor | string | color code
textLine2.backgroundImageAssetSid | string | image asset sid
textLine2.opacity | float | text opacity between 0.1 - 1
textLine2.fontColor | string | color code
textLine2.text | string | your text here


## Transcoding Job Notification Object Structure

```
{
    "allJobsFinished": false,
    "assetId": "56f291a200ddb30a028b46af",
    "assetSid": "7BbLrskb",
    "callBackUrl": "http://httpbin.org/post",
    "creationTime": 1458737573690,
    "errorCode": null,
    "errorMessage": null,
    "id": "56f291a500ddb374068b5006",
    "lastUpdatedTime": 1458737721787,
    "progress": 74,
    "sid": "7BbLrCPJ",
    "startTime": 1458737637473,
    "state": "PROGRESSING",
    "template": {
        "audioBitrate": 128,
        "audioChannels": 2,
        "audioCodec": "libfdk_aac",
        "audioSampleRate": 44100,
        "bufferSize": null,
        "constantRatefactor": null,
        "container": "mp4",
        "creationTime": 1457964080907,
        "fixedNumberOfFramesBetweenKeyframes": null,
        "frameRate": "29.97",
        "id": "56e6c43000ddb33a5c8b4b14",
        "maxBitRate": null,
        "maxHeight": 480,
        "maxWidth": 854,
        "maximumNumberOfFramesBetweenKeyframes": null,
        "rateControl": "targetBitrate",
        "replacing": null,
        "transmuxToHls": null,
        "type": "VIDEO",
        "videoBitrate": 1200,
        "videoCodec": "libx264",
        "videoCodecOptions": {},
        "videoMaxFrameRate": null
    },
}
```

Parameter | Type | Description
--------- | ------- | -----------
id | string | job id
allJobsFinished | boolean | asset could have several trancoding jobs and each job produces a conversion which is a video, audio or image object. allJobsFinished property indicates all jobs finished and all conversions are ready. Usually value of this parameter is true only on the last call.
progress | number | completed percentage of the job
state | enum | status of the job, could be one of INITIAL PROGRESSING COMPLETED ERROR
assetId | string | indicates the asset id this jobs is working on
assetSid | string | indicates the asset short id this jobs is working on
callBackUrl | string | it is the url where this object is sent
creationTime | number | job creation time in seconds since the Unix epoch
startTime | number | job start time in seconds since the Unix epoch
lastUpdatedTime | number | job last updated time in seconds since the Unix epoch
errorCode | string | error code if job is failed
errorMessage | string | error message if job is failed
template | mixes | template object

## Video Transcoding Template Object Structure
```
{
        "audioBitrate": 128,
        "audioChannels": 2,
        "audioCodec": "libfdk_aac",
        "audioSampleRate": 44100,
        "bufferSize": null,
        "constantRatefactor": null,
        "container": "mp4",
        "creationTime": 1457964080907,
        "fixedNumberOfFramesBetweenKeyframes": null,
        "frameRate": "29.97",
        "id": "56e6c43000ddb33a5c8b4b14",
        "maxBitRate": null,
        "maxHeight": 480,
        "maxWidth": 854,
        "maximumNumberOfFramesBetweenKeyframes": null,
        "rateControl": "targetBitrate",
        "replacing": null,
        "transmuxToHls": false,
        "type": "VIDEO",
        "videoBitrate": 1200,
        "videoCodec": "libx264",
        "videoCodecOptions": {
            "level": "3.1", 
            "maxReferenceFrames": "6", 
            "profile": "main"
        }
        "videoMaxFrameRate": null
    }
```
Parameter | Type | Description
--------- | ------- | -----------
id | string | template id
<b>type</b> | enum | template type, could be VIDEO, AUDIO, IMAGE or LIVE.
<b>maxWidth</b> | number | The maximum width of the output video in pixels. Set an even integer between 128 and 4096. This template will be ignored in case width of the source video is less than the specified value unless allowScaleUp parameter is set to true.
<b>maxHeight</b> | number | The maximum height of the output video in pixels. Set an even integer between 96 and 3072. This template will be ignored in case height of the source video is less than the specified value unless allowScaleUp parameter is set to true.
allowScaleUp | boolean | When set to false template gets ignored in case the source video resolution requires to be scaled up at the given parameters of maxWidth and maxHeight. When set to true, template gets forced to process the given parameters of maxWidth and maxHeight. 
container | string | The container type for the output file. Valid values are MP4, WEBM, HLS.
transmuxToHls | boolean | Applicable only MP4 container is selected. When set to true an additional transcoding job is created to generate hls segments.
videoCodec | string | The video codec for the output file. Valid values are libx264, and vp8.
rateControl | string | You can configure variable bit rate or constant bit rate encoding, valid values are constantQuality, targetBitrate.
constantRatefactor | number | Specify in case constantQuality is selected on rateControl parameter.
videoBitrate | number | The kilobit rate of the audio stream in the output file, in kilobits/second. Specify a value between 16 and 8092.
videoCodecOptions | object | Applicable only when videoCodec is libx264 or vp8. 
videoCodecOptions.profile | string | Specify h264 or vp8 codec encoding profile. Specify the following profiles for H264 : baseline: The profile most commonly used for mobile applications. main: The profile used for standard-definition digital TV broadcasts. high: The profile used for high-definition digital TV broadcasts.When the video codec is VP8 possible values are 0, 1, 2, and 3.
videoCodecOptions.level | string | The H.264 level that you want to use for the output video. 
videoCodecOptions.maxReferenceFrames | string | The maximum number of previously decoded frames to use as a reference for decoding future frames.
fixedNumberOfFramesBetweenKeyframes | boolean | Whether to use a fixed value for maximumNumberOfFramesBetweenKeyframes. Yes: Transcoder uses the value of maximumNumberOfFramesBetweenKeyframes for the distance between key frames (the number of frames in a group of pictures, or GOP). No: The distance between key frames can vary.
maximumNumberOfFramesBetweenKeyframes | number | aka keyframe interval, sets the maximum number of frames between each keyframe. Specifying a keyframe interval will allow you to create more or less keyframes in your video. For example, a value of 100 will create a keyframe every 100 frames.
bufferSize | number | The maximum number of kilobits in any x seconds of the output video. 
maxBitRate | number | The maximum number of kilobits per second in the output video. Specify a value between 16 and 8092.
<b>frameRate</b> | string | The frames per second for the video stream in the output video. Could be one of auto, 10, 15, 23.97, 24, 25, 29.97, 50, or 60.
videoMaxFrameRate | number | Transcoder uses the frame rate of the input video for the frame rate of the output video up to specified value for videoMaxFrameRate. 
audioSampleRate | string | The sample rate of the audio stream in the output file, in Hz.
audioBitrate | number | The kilobit rate of the audio stream in the output file, in kilobits/second. Specify a value between 64 and 320.
audioChannels | string | The number of audio channels in the output file.
audioCodec | string | The audio codec for the output file. Valid values are libfdk_aac, mp3.
creationTime | number | job creation time in seconds since the Unix epoch

### Video Transcoding Template Validations

Extends <a href="#audio-transcoding-template-validations">Audio Transcoding Template Validations</a>

Parameter | Validations
--------- | -----------
videoCodec | Required
maxWidth | Required, Between (128, 4096)
maxHeight | Required, Between (96, 3072)
frameRate | Required, enum Alpha Numeric Chars ('auto', '10', '15', '23.97', '24', '25', '29.97', '30', '50', '60')
videoBitrate | Required if rateControl equal to targetBitrate, Between (16, 8092)
constantRatefactor | Required if rateControl equal to constantQuality, Between (15, 45)
videoCodecOptions.profile | Required if videoCodec equal to libx264, could be one of 'baseline', 'main', 'high'
videoCodecOptions.maxReferenceFrames | Required if videoCodec equal to libx264, Between (0, 16)
videoCodecOptions.level | Required if videoCodec equal to libx264, could be one of '1', '1b', '1.1', '1.2', '1.3', '2', '2.1', '2.2', '3', '3.1', '3.2', '4', '4.1'

## Live Transcoding Template Object Structure
```
{
        "audioBitrate": 128,
        "audioChannels": 2,
        "audioCodec": "libfdk_aac",
        "audioSampleRate": 44100,
        "constantRatefactor": 23,
        "creationTime": 1457964080907,
        "fixedNumberOfFramesBetweenKeyframes": true,
        "frameRate": "29.97",
        "maxBitRate": null,
        "maxHeight": 480,
        "maxWidth": 854,
        "maximumNumberOfFramesBetweenKeyframes": null,
        "rateControl": "constantQuality",
        "type": "LIVE",
        "videoCodec": "libx264",
        "videoCodecOptions": {
            "level": "3.1", 
            "maxReferenceFrames": "6", 
            "profile": "main"
        }
    }
```
Parameter | Type | Description
--------- | ------- | -----------
id | string | template id
<b>type</b> | enum | template type, could be VIDEO, AUDIO, IMAGE or LIVE.
<b>maxWidth</b> | number | The maximum width of the output video in pixels. Set an even integer between 128 and 4096. This template will be ignored in case width of the source video is less than the specified value.
<b>maxHeight</b> | number | The maximum height of the output video in pixels. Set an even integer between 96 and 3072. This template will be ignored in case height of the source video is less than the specified value.
videoCodec | string | The video codec for the output file. libx264 is mandatory.
rateControl | string | At live template this value is fixed as "constantQuality".
constantRatefactor | number | At live template this value is fixed as 23.
videoCodecOptions | object | Applicable only when videoCodec is libx264. 
videoCodecOptions.profile | string | Specify h264 codec encoding profile. Specify the following profiles for H264 : baseline: The profile most commonly used for mobile applications. main: The profile used for standard-definition digital TV broadcasts. high: The profile used for high-definition digital TV broadcasts.
videoCodecOptions.level | string | The H.264 level that you want to use for the output video. 
videoCodecOptions.maxReferenceFrames | string | The maximum number of previously decoded frames to use as a reference for decoding future frames.
fixedNumberOfFramesBetweenKeyframes | boolean | At live template this value is fixed as true.
maximumNumberOfFramesBetweenKeyframes | number | aka keyframe interval, sets the maximum number of frames between each keyframe. Specifying a keyframe interval will allow you to create more or less keyframes in your video. For example, a value of 100 will create a keyframe every 100 frames.
maxBitRate | number | The maximum number of kilobits per second in the output video. Specify a value between 16 and 8092.
<b>frameRate</b> | string | The frames per second for the video stream in the output video. Could be one of auto, 10, 15, 23.97, 24, 25, 29.97, 50, or 60.
audioSampleRate | string | The sample rate of the audio stream in the output file, in Hz.
audioBitrate | number | The kilobit rate of the audio stream in the output file, in kilobits/second. Specify a value between 64 and 320.
audioChannels | string | The number of audio channels in the output file.
audioCodec | string | The audio codec for the output file. libfdk_aac is mandatory.
creationTime | number | job creation time in seconds since the Unix epoch

### Live Transcoding Template Validations

Extends <a href="#video-transcoding-template-validations">Video Transcoding Template Validations</a>

## Audio Transcoding Template Object Structure

```
{
    "audioBitrate":64,
    "audioChannels":2,
    "audioCodec":"libfdk_aac",
    "audioSampleRate":44000,
    "container":"aac",
    "type":"AUDIO"
}
```

Parameter | Type | Description
--------- | ------- | -----------
id | string | template id
<b>type</b> | enum | template type, could be VIDEO AUDIO IMAGE
audioBitrate | string | The bit rate of the audio stream in the output file, in kilobits/second. Specify a value between 64k and 320k.
audioChannels | string | The number of audio channels in the output file.
audioCodec | string | The audio codec for the output file. Valid values are libfdk_aac, mp3.
audioSampleRate | string | The sample rate of the audio stream in the output file, in Hz.
<b>container</b> | string | The container type for the output file. Valid values are AAC, MP3.

### Audio Transcoding Template Validations

Parameter | Validations
--------- | -----------
container | Required, Alpha Numeric
audioCodec | Required
audioChannels | Required, enum Digits (0, 1, 2)
audioBitrate | Required, Digits
audioSampleRate | Required, enum Digits (22050, 32000, 44100, 48000, 96000)

## Image Transcoding Template Object Structure
```
{
    "type":"IMAGE",
    "singleSnapshotSecond":null,
    "snapshotIntervalSecond":null,
    "stripeIntervalSecond":5,
    "snapshotCount":4,
    "maxHeight":480,
    "maxWidth":640,
    "container":"jpg"
}
```
Parameter | Type | Description
--------- | ------- | -----------
id | string | template id
<b>type</b> | enum | template type, set to IMAGE for image generation.
singleSnapshotSecond | number | Specify if one thumbail is required at specific duration of video. Keep blank if you want transcoder to ignore this.
snapshotIntervalSecond | number | Specify an interval duration to capture thumbnails from video. Keep blank if you want transcoder to ignore this. 
stripeIntervalSecond | number | Specify an interval duration to generate sprite images used on the player scrub bar. Keep blank if you want transcoder to ignore this.
snapshotCount | number | Specify the total amount of thumnails to be generated, api decices where to cut the video. Keep blank if you want transcoder to ignore this.
<b>maxHeight</b> | number | Specify the maximum height of the image you need to generate.
<b>maxWidth</b> | number | Specify the maximum width of the image you need to generate.
<b>container</b> | enum | The container type for the output file. Valid values are jpg, png.

### Image Transcoding Template Validations

Parameter | Validations
--------- | -----------
container | Required, Valid values are jpg, png.
maxWidth | Required, Between (128, 4096)
maxHeight | Required, Between (96, 3072)

## File Object Structure
```
{
    "id": "56f3f28500ddb372068b5166",
    "sid": "7Bd9gypt",
    "type": "IMAGE",
    "size": 210606,
    "tags": [],
    "status": null,
    "container": "jpg",
    "contentType": "video/mp4",
    "creationTime": 1458742871986
}
```
Parameter | Type | Description
--------- | ------- | -----------
id | string | file reference id
sid | string | file reference short id
type | enum | IMAGE|AUDIO|VIDEO|OTHER
size | 210606 | file size of bytes
tags | array | file tags
status | enum | status of file
container | string | file extension mp4, ts, jpg, png, bmp ...etc
contentType | string | file mime type for example: video/mp4, audio/aac, image/jpeg, image/png
creationTime | long | creation time of milliseconds

## Image File Object Structure (Extends <a href="#file-object-structure">file</a> Object Structure)
```
{
    "width": 640,
    "height": 360
}
```
Parameter | Type | Description
--------- | ------- | -----------
width | integer | image width
height | integer | image height

## Video File Object Structure (Extends <a href="#file-object-structure">file</a> Object Structure)
```
{
    "width": 854,
    "height": 480,
    "audioBitrate": 128,
    "audioChannels": 2,
    "audioCodec": "libfdk_aac",
    "audioSampleRate": 44100,
    "duration": 287.578333,
    "frameRate": "29.97",
    "videoBitrate": 1200,
    "videoCodec": "libx264"
}
```
Parameter | Type | Description
--------- | ------- | -----------
width | integer | video width
height | integer | video height
audioBitrate | float | bitrate of audio
audioChannels | integer | audo channels count 1,2 -> mono stereo
audioCodec | string | codec of audio
audioSampleRate | float | sample rate of audio for example 44.100
duration | float | video duration of seconds
frameRate | float | video frame rate
videoBitrate | float | bitrate of video
videoCodec | string | codec of video

## Audio File Object Structure (Extends <a href="#file-object-structure">file</a> Object Structure)
```
{
    "audioBitrate": 128,
    "audioChannels": 2,
    "audioCodec": "libfdk_aac",
    "audioSampleRate": 44100,
    "duration": 287.578333
}
```
Parameter | Type | Description
--------- | ------- | -----------
audioBitrate | float | bitrate of audio
audioChannels | integer | audo channels count 1,2 -> mono stereo
audioCodec | string | codec of audio
duration | float | video duration of seconds
audioSampleRate | float | sample rate of audio for example 44.100

## Transcoding Job Object Structure
```
{
    "id": "56f3f28500ddb372068b516d",
    "template": {
      "type": "VIDEO",
      "audioBitrate": 128,
      "audioChannels": 2,
      "audioCodec": "libfdk_aac",
      "audioSampleRate": 44100,
      "frameRate": "29.97",
      "videoBitrate": 1200,
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
    "errorCode": null,
    "errorMessage": null,
    "state": "COMPLETE",
    "progress": 100,
    "conversionId": "56f3f28500ddb372068b516c"
}
```
Parameter | Type | Description
--------- | ------- | -----------
id | string | Transcoding job id
template | object | <a href="#video-transcoding-template-object-structure">videoConversionTemplate</a>, <a href="#audio-transcoding-template-object-structure">audioConversionTemplate</a> or <a href="#image-transcoding-template-object-structure">imageConversionTemplate</a> object
creationTime | long | creation time of milliseconds
startTime | long | job start time of milliseconds
lastUpdatedTime | long | job updated time of milliseconds
state | enum | (QUEUE,STARTED,PROGRESSING,COMPLETE,WARNING,ERROR,CANCELED,TIMEOUT)
progress | float | job progressing percentage 0 to 100
errorCode | string | if throws an error
errorMessage | string | if throws an error
conversionId | string | conversion reference id for only completed job

## Social Buttons Object Structure
```
{
    "scalar": false,
    "facebook": true,
    "twitter": true,
    "google": true,
    "pinterest": true,
    "linkedIn": true
}
```
Parameter | Type | Description
--------- | ------- | -----------
scalar | boolean | show scalar button status
facebook | boolean | sharing on facebook
twitter | boolean | sharing on twitter
google | boolean | sharing on google
pinterest | boolean | sharing on pinterest
linkedIn | boolean | sharing on linked-in

## Player Ads Ad Tag Uri Object Structure
```
{
  "weight": 100,
  "uri": "https://googleads.g.doubleclick.net/pagead/ads?...xml_vast3"
}
```
Parameter | Type | Description
--------- | ------- | -----------
weight | long | weight for uri
uri | string | ads uri

## Player Ads Ad Break Object Structure
```
{
  "breakType": 100,
  "timeOffset": "",
  "allowMultipleAds": false,
  "followRedirects": true,
  "adTagUri": [
      {
        "weight": 100,
        "uri": "https://googleads.g.doubleclick.net/_vast3"
      }
  ]
}
```
Parameter | Type | Description
--------- | ------- | -----------
breakType | enum | (LINEAR, NON_LINEAR, DISPLAY)
timeOffset | string | time offset
allowMultipleAds | boolean | allowed multiple ads if true
followRedirects | boolean | following uri redirects
adTagUri | array | <a href="#player-ads-ad-tag-uri-object-structure">adTagUriObject</a> each one

## Player Ads Object Structure
```
{
    "id": "56e1cd6300ddb31a5c8b4674",
    "sid": "7AU2sjb9",
    "title": "IMA Test",
    "type": "URI",
    "adTagUri": [
        {
          "weight": 100,
          "uri": "https://googleads.g.doubleclick.net/pagead/ads?...xml_vast3"
        }
    ],
    "adBreaks": [],
    "creationTime": 1457638755757
}
```
Parameter | Type | Description
--------- | ------- | -----------
id | string | ads id
sid | string | ads short id
title | string | ads title
type | enum | (URI or CUSTOM)
adTagUri | array | <a href="#player-ads-ad-tag-uri-object-structure">adTagUriObject</a> each one
adBreaks | array | <a href="#player-ads-ad-break-object-structure">adBreakObject</a> each one
creationTime | long | creation time of milliseconds

## Player Google Analytics Object Structure
```
{
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
}
```
Parameter | Type | Description
--------- | ------- | -----------
loaded | boolean | loaded event log status
percentsPlayed | boolean | percents played event log status
start | boolean | start event log status
end | boolean | end event log status
seek | boolean | seek event log status
play | boolean | play event log status
pause | boolean | pause event log status
resize | boolean | resize event log status
volumeChange | boolean | volume change event log status
error | boolean | error event log status
fullscreen | boolean | full screen event log status

## Playlist Item Asset Object Structure
```
{
    "id": "532532jf032jf02jf023jf20",
    "sid": "78fd3f32",
    "title": "Asset Title",
    "author": "Copyright NOC INC",
    "tags": ["asset tag 1", "asset tag 2"],
    "viewCounts": 52664,
    "referenceId": "your asset reference id",
    "referenceUrl": "youtube, daily motion, another ...etc",
    "deliveryStatus": "ACTIVE",
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
    }
}
```
Parameter | Type | Description
--------- | ------- | -----------
id | string | asset id
sid | string | asset short id
title | string | asset short id
author | string | asset short id
tags | array | tag each one
viewCounts | long | view counts of asset
referenceId | string | your reference id
referenceUrl | string | your reference url youtube, daily motion, another ...etc
deliveryStatus | enum | (ACTIVE, PASSIVE or SUSPENDED)
source | object | <a href="#image-file-object-structure-extends-file-object-structure">imageFile</a> , <a href="#video-file-object-structure-extends-file-object-structure">videoFile</a>, <a href="#audio-file-object-structure-extends-file-object-structure">audioFile</a>, <a href="#live-source-object-structure">liveSource</a>, <a href="#live-event-source-object-structure">liveEventSource</a>, <a href="#live-pull-source-object-structure">livePullSource</a> object
creationTime | long | creation time of milliseconds

## Playlist Item Object Structure
```
{
    "sort": 154,
    "asset": {
         "id": "532532jf032jf02jf023jf20",
         "sid": "78fd3f32",
         "title": "Asset Title",
         "author": "Copyright NOC INC",
         "tags": ["asset tag 1", "asset tag 2"],
         "viewCounts": 52664,
         "referenceId": "your asset reference id",
         "referenceUrl": "youtube, daily motion, another ...etc",
         "deliveryStatus": "ACTIVE",
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
         }
    },
    "creationTime": 1458742871986
}
```
Parameter | Type | Description
--------- | ------- | -----------
sort | long | item sort
asset | object | <a href="#playlist-item-asset-object-structure">playlistItemAssetObject</a>
creationTime | long | creation time of milliseconds
