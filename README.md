<img src="http://player.kumullus.com/assets/logo.svg" width="15%">

## HTML VIDEO PLAYER

![Build Status][version-image]
[![video.js][videojs-image]][videojs-url]
![Docs Status][docs-image]
[![MIT License][license-image]][license-url]
[![Download][download-image]][download-url]

> A complete HTML/CSS video player that aims to bring interactity to the video 
> Built on top of [video.js](https://github.com/videojs/video.js).
> We strongly recommend to first visit (http://docs.videojs.com/docs/) and get familiar with "video js" before cotinuing using kmlplayer

- [Installation and configuration](#installation-and-configuration)
- [Usage](#usage-and-best-practices)
- [Plugins](#plugins)
- [Demos](#demos)
- [F.A.Q](#frequently-asked-questions)
- [License](#license)
- [Credits and Acknowledgments](#credits-and-acknowledgments)

#### Installation and configuration

__1. Download the package__

Download the [kmlPlayer][download-url] package and move it in your assets folder.

__2. Add Script and Stylesheet__
``` html
<head>
   ...
   <meta name="viewport" content="width=device-width, minimum-scale=1.0, initial-scale=1, maximum-scale=1"/>
   <link rel="stylesheet" type="text/css" href="assets/kmlPlayer/kmlPlayer.min.css">
   ...
</head>
<body>
   ...
   <script src="assets/kmlPlayer/kmlPlayer.min.js"></script>
</body>
```

__2.1 IE8 support__
If you'd like to support IE8, add the following lines inside the head of the page
``` html
<head>
	...
	<!--[if lte IE 9]>
       <script src="assets/ie8/kmlPlayer.min.js"></script>
   <![endif]-->
	...
</head>
```

__3. Add a `<video>` tag__
``` html
<video class="videoWrapper video-js">
   <source type="video/mp4" src="https://cdn.selz.com/plyr/1.5/View_From_A_Blue_Moon_Trailer-HD.mp4"></source>
</video>
```

__4. Instantiate kmlPlayer__
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'));
```

View working example on [codepen](http://codepen.io/lmihaidaniel/pen/WwmBrB)

#### Usage and best practices

``` javascript
var app = {
  initiated: false,
  init: function(){
    if(!this.initiated){
      ....
      this.initiated = true;  
    }
    ....
  },
  scene: 1,
  loadScene: function(){
    this.scene += 1;
    console.log('loading scene '+this.scene);
    ...
  }
}

var myPlayer = kmlplayer(document.querySelector('video'), {
  timeline: {
    responsive: true
  }
}, {
  loadedmetadata: function(){
    app.init();
  },
  end: function(){
    app.loadScene();
  }
});


```

#### Events

- [abort](#eventabort)
- [canplay](#eventcanplay)
- [canplaythrough](#eventcanplaythrough)
- [durationchange](#eventdurationchange)
- [emptied](#eventemptied)
- [ended](#eventended)
- [error](#eventerror)
- [loadeddata](#eventloadeddata)
- [loadedmetadata](#eventloadedmetadata)
- [loadstart](#eventloadstart)
- [pause](#eventpause)
- [play](#eventplay)
- [playing](#eventplaying)
- [progress](#eventprogress)
- [ratechange](#eventratechange)
- [seeked](#eventseeked)
- [seeking](#eventseeking)
- [stalled](#eventstalled)
- [suspend](#eventsuspend)
- [timeupdate](#eventtimeupdate)
- [volumechange](#eventvolumechange)
- [waiting](#eventwaiting)


##### Event abort 
Fires when the loading of an audio/video is aborted
##### Event canplay 
Fires when the browser can start playing the audio/video
##### Event canplaythrough  
Fires when the browser can play through the audio/video without stopping for buffering
##### Event durationchange  
Fires when the duration of the audio/video is changed
##### Event emptied 
Fires when the current playlist is empty
##### Event ended 
Fires when the current playlist is ended
##### Event error 
Fires when an error occurred during the loading of an audio/video
##### Event loadeddata
Fires when the browser has loaded the current frame of the audio/video
##### Event loadedmetadata
Fires when the browser has loaded meta data for the audio/video
##### Event loadstart
Fires when the browser starts looking for the audio/video
##### Event pause
Fires when the audio/video has been paused
##### Event play
Fires when the audio/video has been started or is no longer paused
##### Event playing
Fires when the audio/video is playing after having been paused or stopped for buffering
##### Event progress
Fires when the browser is downloading the audio/video
##### Event ratechange
Fires when the playing speed of the audio/video is changed
##### Event seeked
Fires when the user is finished moving/skipping to a new position in the audio/video
##### Event seeking
Fires when the user starts moving/skipping to a new position in the audio/video
##### Event stalled
Fires when the browser is trying to get media data, but data is not available
##### Event suspend
Fires when the browser is intentionally not getting media data
##### Event timeupdate
Fires when the current playback position has changed * During playback this is fired every 15-250 milliseconds, depending on the playback technology in use.
##### Event volumechange
Fires when the volume has been changed
##### Event waiting
Fires when the video stops because it needs to buffer the next frame
##### Event useractive
Fired when the user is active, e.g. moves the mouse over the player
##### Event userinactive
ired when the user is inactive, e.g. a short delay after the last mouse move or control interaction

#### Plugins

- [Overlays](#overlays)
- [Cuepoints](#cuepoints)
- [Responsive](#responsive)
- [Subtitles](#subtitles)
- [Bounds](#bounds)
- [Visibility](#visibility)
- [SCORM](#scorm)
- [Context menu](#contextmenu)
- [Powered by](#poweredby)
- [Utils](#utils)


##### Overlays

##### Cuepoints

##### Responsive

##### Subtitles

##### Bounds

##### Visibility

##### Context menu

##### Powered by

##### Utils


#### Demos

#### Frequently Asked Questions

__First Question?__

This is the first answer

__Second Question?__

Second answer


#### Credits and Acknowledgments

Created and Maintained by [Mihai Lacatusu](https://github.com/lmihaidaniel)


#### About The Project

* [Changelog](../../blob/master/CHANGELOG.md)
* [GPL](http://opensource.org/licenses/GPL-3.0)


http://player.kumullus.com/

[version-image]:https://img.shields.io/badge/version-1.0.0-green.svg?style=flat-square
[videojs-image]:https://img.shields.io/badge/video.js-5.10.2-green.svg?style=flat-square
[videojs-url]:https://github.com/videojs/video.js
[docs-image]:https://img.shields.io/badge/docs-5%25-orange.svg?style=flat-square
[license-image]:https://img.shields.io/badge/license-GPL-blue.svg?style=flat-square
[license-url]:LICENSE
[download-image]:https://img.shields.io/badge/download-1.0.0-yellowgreen.svg?style=flat-square
[download-url]:https://github.com/lmihaidaniel/kmlplayer/archive/master.zip