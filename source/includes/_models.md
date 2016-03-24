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
prefixAssetSid | mixed | asset sid for prefix
postfixAssetSid | mixed | asset sid for postfix
overlayImages[].assetSid | mixed | image asset sid
overlayImages[].location | enum | TOP_LEFT,TOP_RIGHT,BOTTOM_LEFT,BOTTOM_RIGHT
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
        "audioBitrate": "128k",
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
        "max_width": 854,
        "maximumNumberOfFramesBetweenKeyframes": null,
        "rateControl": "targetBitrate",
        "replacing": null,
        "transmuxToHls": null,
        "type": "VIDEO",
        "videoBitrate": "1200k",
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
        "audioBitrate": "128k",
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
        "max_width": 854,
        "maximumNumberOfFramesBetweenKeyframes": null,
        "rateControl": "targetBitrate",
        "replacing": null,
        "transmuxToHls": null,
        "type": "VIDEO",
        "videoBitrate": "1200k",
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
<b>type</b> | enum | template type, could be VIDEO AUDIO IMAGE
audioBitrate | string | The bit rate of the audio stream in the output file, in kilobits/second. Specify a value between 64k and 320k.
audioChannels | string | The number of audio channels in the output file.
audioCodec | string | The audio codec for the output file. Valid values are libfdk_aac, mp3.
audioSampleRate | string | The sample rate of the audio stream in the output file, in Hz.
bufferSize | string | The maximum number of kilobits in any x seconds of the output video. 
rateControl | string | You can configure variable bit rate or constant bit rate encoding, valid values are constantQuality, targetBitrate.
constantRatefactor | number | specify in case constantQuality is selected on rateControl parameter.
maxBitRate | string | The maximum number of kilobits per second in the output video. Specify a value between 16k and 8092k.
container | string | The container type for the output file. Valid values are MP4, WEBM, HLS.
creationTime | number | job creation time in seconds since the Unix epoch
fixedNumberOfFramesBetweenKeyframes | boolean | Whether to use a fixed value for maximumNumberOfFramesBetweenKeyframes.
frameRate | number | The frames per second for the video stream in the output video.
maxHeight | string | error message if job is failed
maximumNumberOfFramesBetweenKeyframes | mixes | template object
transmuxToHls | boolean | setting this value to true lets the api to generate a second dependant job in order to transmux to hls.
videoBitrate | string | The bit rate of the audio stream in the output file, in kilobits/second. Specify a value between 16k and 8092k.
videoCodec | string | The video codec for the output file. Valid values are libx264, and vp8.
videoCodecOptions | mixes | Applicable only when the value of videoCodec is libx264. 
videoMaxFrameRate | mixes | Api uses the frame rate of the input video for the frame rate of the output video, up to the maximum frame rate. 

## Audio Transcoding Template Object Structure

```
{
    "audioBitrate":"64k",
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
<b>type</b> | enum | template type, could be VIDEO AUDIO IMAGE
singleSnapshotSecond | number | Specify if one thumbail is required at spesific duration of video.
snapshotIntervalSecond | string | Specify an interval duration to capture thumbnails from video.
stripeIntervalSecond | string | Specify an interval duration to generate sprite images used on the player scrub bar.
snapshotCount | string | Specify the total amount of thumnails to be generated, api decices where to cut the video.
<b>maxHeight</b> | string | Specify the maximum height of the image you need to generate.
<b>maxWidth</b> | string | Specify the maximum width of the image you need to generate.
<b>container</b> | string | The container type for the output file. Valid values are jpg, png.

