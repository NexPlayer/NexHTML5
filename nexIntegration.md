<a id="integration-top"> </a>

# NexPlayer™ Integration

This section explains how to integrate NexPlayer&#x2122; for PS4 into your project.

## Sample

Integrating NexPlayer&#x2122; into an  <a href="https://nexplayer.nexplayersdk.com/sample/index.html" download="" target="_blank">HTML5 file</a>:</p>

```html

<!DOCTYPE html>
<html>

<head>
    <!-- MANDATORY! LOAD JQUERY BY CDN OR LOCAL  -->
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <meta name="description" content="Nexplayer"/>
    <title>NexPlayer</title>
</head>

 <style>
    #player_container {
        width: 600px;
        height: 100%;
        margin: auto;
        position: absolute;
    }
 </style>

 <body>
  <div id="player"></div>
  <script src=""Latest SDK version."></script>
 </body>

 <script type="text/javascript">
    var player = new nexplayer.NexPlayer();

    player.init({
        key: 'ENTER YOUR LICENSE KEY HERE',
        div: document.getElementById("player"),
        src: 'https://livesim.dashif.org/dash/vod/testpic_2s/multi_subs.mpd',
    });
</script>

</html>
```

<div class="alert alert-success hints-alert"><div class="hints-icon"><i class="fa fa-mortar-board"></i></div><div class="hints-container"><p>Please note that replacing the license key is mandatory. License key should have been already sent to your inbox or you can request one from support.madrid@nexplayer.com. </p>
</div></div>

## Step-by-Step

To integrate NexPlayer™ into your project you must complete the following steps:

- The NexPlayer™ JavaScript library should be included in the HTML file:

```html
<script src="Latest SDK version."></script>
```

<div class="alert alert-success hints-alert"><div class="hints-icon"><i class="fa fa-mortar-board"></i></div><div class="hints-container"><p>Please note that the use of https to call our library is mandatory. <br>
</div></div>

- A div that will contain the video and the UI has to be declared:
```html
<body>
...
    <div id="player"></div>
...
</body>
```
- The player should be initialized by entering the previous div to the init or setup methods:
    > nexplayer.Setup
    ```js
        var player = nexplayer.Setup({
            key: 'ENTER YOUR LICENSE KEY HERE',
            div: document.getElementById("player"),
            src: 'https://livesim.dashif.org/dash/vod/testpic_2s/multi_subs.mpd',
        });
    ```
    > player.init
    ```js
        var player = new nexplayer.NexPlayer();
        player.init({
            key: 'ENTER YOUR LICENSE KEY HERE',
            div: document.getElementById("player"),
            src: 'https://livesim.dashif.org/dash/vod/testpic_2s/multi_subs.mpd',
        });
    ```

## Configuration

There are a substantial number of customizable options for NexPlayer™ including: DRM information, VAST link, thumbnails, subtitles, among others.

```js
    key: 'License key to validate the playback', // Mandatory
    div: document.getElementById('player'), // Mandatory
    src: 'URL video', // Mandatory
    drm: [{
        NexDRMType:'DRM Type (eg. com.widevine.alpha(', NexDRMKey: 'URI for the DRM Key', 
        NexHeaders:[{FieldName: 'Header Field Name', FiledValue: 'Header Field Value'}],
        NexCallback:OptionalDRMCallbackForFairPlay
    }], // Optional
    addRequestFilter: Function, // Optional, used for give filters to the drm request
    adsParamsToEncode: Array<string>, // Optional, used to encode adURL parameters
    adURL: string, // Optional
    autoplay: true, // Optional
    callbacksForPlayer: callback, // Optional callback called with the player instances
    captionDisplayer: ICaptionsDisplayer, // Optional
    debug: true, // Optional
    externalSubtitles: {
        src: "URL for the subtitles file",
        language: "Subtitle language",
    }, // Optional
    mutedAtStart: true, // Optional    
    resumePosition: number, // Optional, used for starting the video from the given position in seconds.
    thumbnails: {
         canvas: HTMLCanvasElement; // Mandatory
         urlVtt: "VTT URL"; // Optional
         urlImg: "string"; // Optional
         chunkLimit: number; // Optional
         chunkTotal: number; // Optional
    }, // Optional 
    trailer: boolean, // Optional, false by default. 
    // Set to true when a stream should be considered a trailer, false when not.
    useNewRelicTracker: boolean, // Optional, false by default
    // You need the tracker library in order to be able to use the tracker. Ask NexPlayer team for it.
    vast: 'URL with a VAST/VPAID/VMAP advertisement', // Optional
```