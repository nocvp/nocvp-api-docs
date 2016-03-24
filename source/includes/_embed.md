# Howto Embed
Two types of embed type is supported, with script tag and with iframe tag, we are recommending you to use iframe tag in order to prevent the conflicts. 

Following url could be generated using the defined variables described below for embedding an asset.

http://{content.nocvp.com}/asset/{assetSid}/{playerSid}.[js|html]

{content.nocvp.com} : content.nocvp.com is the generic embed domain, you may use your own by defining a CNAME to content.nocvp.com, but before doing this you need to apply to our support team for the confirmation.
{assetSid} : This is the short id of the asset, please refer to the asset section.
{playerSid} : This is the short id of the player, please refer to the player section.

Following url could be generated using the defined variables described below for embedding a playlist.

http://{content.nocvp.com}/playlist/{playlistSid}/{playerSid}.[js|html]

{playlistSid} : This is the short id of the playlist, please refer to the playlist section.
{playerSid} : This is the short id of the player, please refer to the player section.



##Public Asset Embed
Use the following tags for assets which the privacy is set to PUBLIC.

###With Script Tag

```
<script src="http://{content.nocvp.com}/asset/{assetSID}/{playerSID}.js"></script>
```

###With Iframe Tag

```
<iframe src="http://{content.nocvp.com}/asset/{assetSID}/{playerSID}.html" width="640" height="360" style="border:none;overflow: hidden;" allowfullscreen="true"></iframe>
```


##Private Asset Embed
Use the following tags for assets which the privacy is set to PRIVATE.

###With Script Tag

```
<script src="http://{content.nocvp.com}/asset/{assetSID}/{playerSID}.js?as=assetsigniture&ps=playersigniture&exp=unixtime"></script>
```

###With Iframe Tag

```
<iframe src="http://{content.nocvp.com}/asset/{assetSID}/{playerSID}.html?as=assetsigniture&ps=playersigniture&exp=unixtime" width="640" height="360" style="border:none;overflow: hidden;" allowfullscreen="true"></iframe>
```

#### Howto Generate the query string parameters
as : Asset signature, simply use the formula md5({assetSid}+expiration+{assetId}) to calculate. It is mandatory in case your playlist's privacy is set to PRIVATE.

ps : Player signature, simply use the formula md5(playerSid+expiration+playerId) to calculate. It is mandatory in case your player's privacy is set to PRIVATE.

exp : Unixtime, it is the expiration time in seconds since from Unix epoch, it is mandatory if your player of playlist object's privacy value is PRIVATE.



##Public Playlist Embed
Use the following tags for embedding playlists which are the privacy is set to PUBLIC.

###With Script Tag

```
<script src="http://{content.nocvp.com}/playlist/{playlistSID}/{playerSID}.js"></script>
```

###With Iframe Tag

```
<iframe src="http://{content.nocvp.com}/playlist/{playlistSID}/{playerSID}.html" width="640" height="360" style="border:none;overflow: hidden;" allowfullscreen="true"></iframe>
```


##Private Playlist Embed
Use the following tags for embedding playlists which are the privacy is set to PRIVATE.

###With Script Tag

```
<script src="http://{content.nocvp.com}/playlist/{playlistSID}/{playerSID}.js?as=playlistsigniture&ps=playersigniture&exp=unixtime"></script>
```

###With Iframe Tag

```
<iframe src="http://{content.nocvp.com}/playlist/{playlistSID}/{playerSID}.html?as=playlistsigniture&ps=playersigniture&exp=unixtime" width="640" height="360" style="border:none;overflow: hidden;" allowfullscreen="true"></iframe>
```

#### Howto Generate the query string parameters
as : Playlist signature, simply use the formula md5({playlistSid}+expiration+{playlistId}) to calculate. It is mandatory in case your playlist's privacy is set to PRIVATE.

ps : Player signature, simply use the formula md5(playerSid+expiration+playerId) to calculate. It is mandatory in case your player's privacy is set to PRIVATE.

exp : Unixtime, it is the expiration time in seconds since from Unix epoch, it is mandatory if your player of playlist object's privacy value is PRIVATE.

