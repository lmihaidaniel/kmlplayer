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

- [abort](#event-abort)
- [canplay](#event-canplay)
- [canplaythrough](#event-canplaythrough)
- [durationchange](#event-durationchange)
- [emptied](#even-temptied)
- [ended](#event-ended)
- [error](#event-error)
- [loadeddata](#event-loadeddata)
- [loadedmetadata](#event-loadedmetadata)
- [loadstart](#event-loadstart)
- [pause](#event-pause)
- [play](#event-play)
- [playing](#event-playing)
- [progress](#event-progress)
- [ratechange](#event-ratechange)
- [seeked](#event-seeked)
- [seeking](#event-seeking)
- [stalled](#event-stalled)
- [suspend](#event-suspend)
- [timeupdate](#event-timeupdate)
- [volumechange](#event-volumechange)
- [waiting](#event-waiting)


##### Event abort 
Fires when the loading of an audio/video is aborted
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  abort: function(){
    // this - refers to the player instance;
    console.log(this);
    console.log('audio/video aborted');
  },
  ...
});
```
##### Event canplay 
Fires when the browser can start playing the audio/video
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  canplay: function(){
    // this - refers to the player instance;
    console.log(this);
    console.log('can start playing');
  },
  ...
});
```
##### Event canplaythrough  
Fires when the browser can play through the audio/video without stopping for buffering
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  canplaythrough: function(){
    // this - refers to the player instance;
    console.log(this);
    console.log('can play through');
  },
  ...
});
```
##### Event durationchange  
Fires when the duration of the audio/video is changed
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  durationchange: function(d){
    // this - refers to the player instance;
    console.log('duration changed to', d);
  },
  ...
});
```
##### Event emptied 
Fires when the current playlist is empty
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  emptied: function(){
    // this - refers to the player instance;
    console.log(this);
    console.log('current playlist is empty');
  },
  ...
});
```
##### Event ended 
Fires when the current playlist is ended
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  ended: function(){
    // this - refers to the player instance;
    console.log(this);
    console.log('video ended');
    /* 
      Best practice
      =============
      When building a sequence of videos is best to use this event to trigger your app to load a new video sequence
    */
  },
  ...
});
```
##### Event error 
Fires when an error occurred during the loading of an audio/video
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  error: function(e){
    // this - refers to the player instance;
    console.log(this);
    console.log('error loading the media, error', e);
  },
  ...
});
```
##### Event loadeddata
Fires when the browser has loaded the current frame of the audio/video
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  loadeddata: function(){
    // this - refers to the player instance;
    console.log(this);
    console.log('loaded the current frame');
  },
  ...
});
```
##### Event loadedmetadata
Fires when the browser has loaded meta data for the audio/video
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  loadedmetadata: function(){
    // this - refers to the player instance;
    console.log(this);
    console.log('loadeded metadata');
     /* 
      Best practice
      =============
      When building a sequence of videos is best to use this event to trigger your app to initate a new sequence so that you will have access to the new parameters of the video
      video width: this.videoWidth();
      video height: this.videoHeight();

      Also clean the current sequence content when needed before initating the new sequence

      You can use flags on the player so that whenever a new video is loaded some part of your app logic is triggered only once. Eg:
      if(!this._myFlag){
        app.doSomethingOnce(); // best for global elements, logic or events that should persist in all the sequences
        this._myFlag = true;
      }
    */
  },
  ...
});
```
##### Event loadstart
Fires when the browser starts looking for the audio/video
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  loadeddata: function(){
    // this - refers to the player instance;
    console.log(this);
    console.log('start looking for the audio/video');
    /* 
      Best practice
      =============
      When building a sequence of videos is best to use this event to trigger your app to clean previous logic/elements
      Clean the current sequence content when needed before initating the new sequence in loadedmetadata
    */
  },
  ...
});
```
##### Event pause
Fires when the audio/video has been paused
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  pause: function(){
    // this - refers to the player instance;
    console.log(this);
    console.log('media paused');
    /* 
      Best practice
      =============
      Use this event to easily integrate your own video controls
    */
  },
  ...
});
```
##### Event play
Fires when the audio/video has been started or is no longer paused
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  play: function(){
    // this - refers to the player instance;
    console.log(this);
    console.log('media start playing');
    /* 
      Best practice
      =============
      Use this event to easily integrate your own video controls
    */
  },
  ...
});
```
##### Event playing
Fires when the audio/video is playing after having been paused or stopped for buffering
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  playing: function(){
    // this - refers to the player instance;
    console.log(this);
    console.log('media playing');
    /* 
      Best practice
      =============
      Use this event to easily integrate your own video controls
    */
  },
  ...
});
```
##### Event progress
Fires when the browser is downloading the audio/video
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  progress: function(){
    // this - refers to the player instance;
    console.log(this);
    console.log('downloading portion of video, buffering');
  },
  ...
});
```
##### Event ratechange
Fires when the playing speed of the audio/video is changed
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  ratechange: function(r){
    // this - refers to the player instance;
    console.log(r); //get the new playback speed
    console.log('playing speed of the media is changed');
  },
  ...
});
```
##### Event seeked
Fires when the user is finished moving/skipping to a new position in the audio/video
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  seeked: function(t){
    // this - refers to the player instance;
    console.log('media moved to the position ', t);
  },
  ...
});
```
##### Event seeking
Fires when the user starts moving/skipping to a new position in the audio/video
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  seeking: function(t){
    // this - refers to the player instance;
    console.log('media moved to the position ', t);
  },
  ...
});
```
##### Event stalled
Fires when the browser is trying to get media data, but data is not available
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  stalled: function(){
    // this - refers to the player instance;
    console.log('media data is not available ');
  },
  ...
});
```
##### Event suspend
Fires when the browser is intentionally not getting media data
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  suspend: function(){
    // this - refers to the player instance;
    console.log('intentionally not getting media data');
  },
  ...
});
```
##### Event timeupdate
Fires when the current playback position has changed * During playback this is fired every 15-250 milliseconds, depending on the playback technology in use.
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  timeupdate: function(t){
    // this - refers to the player instance;
    console.log('current playback position ', t);
  },
  ...
});
```
##### Event volumechange
Fires when the volume has been changed
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  volumechange: function(v){
    // this - refers to the player instance;
    console.log('current media volume ', v);
  },
  ...
});
```
##### Event waiting
Fires when the video stops because it needs to buffer the next frame
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  waiting: function(){
    // this - refers to the player instance;
    console.log('media stopped because it needs to buffer');
  },
  ...
});
```
##### Event useractive
Fired when the user is active, e.g. moves the mouse over the player
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  useractive: function(){
    // this - refers to the player instance;
    console.log('user is active');
  },
  ...
});
```
##### Event userinactive
Fired when the user is inactive, e.g. a short delay after the last mouse move or control interaction
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'), {
    //settings
}, {
  //events
  ...,
  userinactive: function(){
    // this - refers to the player instance;
    console.log('user is inactive');
  },
  ...
});
```

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
Create and add video overlays to the current video.
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'));
var myOverlay = myPlayer.overlays.add({
  id: 'overlay_0', // if not set it will automatically generated
  x: 20, // horizontal position inside the video
  y: 20, // vertical position inside the video
  width: 110, // If given it will set the width size of the overlay - this will adapt according to the video current size;
  height: 110, // If given it will set the height size of the overlay - this will adapt according to the video current size;
  origin: "topLeft", // values accepted : topLeft, top, topRight, left, center, right, bottomLeft, bottom, bottomRight - sets the center point(x,y) position of the marker, defaults to 'topLeft'
  start: 0, // optional defaults to 0 - set when the overlay should start to be visible
  end: -1, //optional defaults to -1 - set when the overlay should be hidded. When set to -1 it makes the overlay visible till the end of the video after the given start
  className: null, // accepts a string or an array of strings - add (a) className(s) to the overlay
  onShow: null || function(e){
    console.log(this); // overlay instance
    console.log(e); // mouse event
  }, // callBack when the overlay is shown
  onHide: null || function(e){
    console.log(this); // overlay instance
    console.log(e); // mouse event
  }, // callBack when the overlay is hided
  onMouseEnter: null || function(e){
    console.log(this); // overlay instance
    console.log(e); // mouse event
  }, // callBack when the mouse entered the overlay
  onMouseMove: null || function(e){
    console.log(this); // overlay instance
    console.log(e); // mouse event
  },  // callBack when the mouse is moving inside the overlay
  onMouseLeave: null || function(e){
    console.log(this); // overlay instance
    console.log(e); // mouse event
  },   // callBack when the mouse is leaving the overlay
  onClick: null || function(e){
    console.log(this); // overlay instance
    console.log(e); // mouse event
  }, // callBack when the overlay is cliked/tapped
  content: null, // accepts a domElement or a function that should return a domElement
  font: {
      min: 1, // multiply the font by x. the font will be set in em units by default.
      ratio: 1, // min font (em units)
      lineHeight: "auto", // auto or lineHeight ratio.
      units: "em"  // rem, em or px
  },
  path: false, // optional: provide an array of coordonates to animate/sync the overlay to the video currentTime, [..., {x:10, y: 10, start: 10, end: 11}, ...]
  visible: false // if not set it will be automaticaly defined by the start and end timings set
});

myOverlay.el_; // get the dom element of the overlay added;
myOverlay.id; // get the id of the overlay added;
myOverlay.addClass; // add a className to the overlay;
myOverlay.removeClass; // remove a className to the overlay;
myOverlay.hasClass; // check if the overlay has a className;
myOverlay.toggleClass; // toggle a current className of the overlay;
myOverlay.content(); // get the content added to the overlay in settings;
myOverlay.trigger('hide','show','click'); // trigger 'onHide','onShow','onClick' added to the overlay in settings;
myOverlay.resize(); // resize this overlay relative to the video current size and position;
myOverlay.font(); // change the font of the overlay relative to the video current size and position;
myOverlay.originPoint(); // gets or sets the center point of the overlay
myOverlay.show(); // makes the overlay visible and sets the visible prop to true
myOverlay.hide(); // hides the overlay and sets the visible prop to false
myOverlay.destroy(); // destroy the currnet overlay and remove it from the player's overlays list

//overlays methods

myPlayer.overlays.add({}); // add an overlay to the player
myPlayer.overlays.show(); // displays all the overlays added; also triggers overlays.onSHow
myPlayer.overlays.hide(); // hides all the overlays added; also triggers overlays.onHide

myPlayer.overlays.el(); // get the overlays wrapper element inside the video player;

myPlayer.overlays.instances( id ); //gets all overlays or specific one by id;

myPlayer.overlays.destroy(); // removes all the overlays from the player and from the memory

myPlayer.overlays.resize(); // resize the overlays relative to the video current size and position;

myPlayer.overlays.suspend(); // stops updating the position and size of the overlays on the video
myPlayer.overlays.process(); // reinits and updates the position and size of the overlays on the video. It is automacally triggered when addind an overlay with overlays.add(...);

```

##### Cuepoints
Add time based cuepoints to the media element of the video. It can have visual representation on a given domElemtn, by default they are set directly inside the timeline of the player's controllBar
``` javascript
myCuepoint = myPlayer.cuepoints.add({
  once: false,  // if true the action will be triggered only once
  start: 0,  // starting time,
  end: -1,  // ending time,
  onStart: function() {}, // callback function triggered on cuepoint start
  onEnd: function() {}, // callback function triggered on cuepoint end
  onClick: function() {},  // callback function triggered when the visual representation is set and clicked
  params: {}, // general parameters that are sent to the cuepoint's callback functions. Best use in conjonction with an app general settings file.
  active: 'active', //name of the class to be added when the cuepoint is active
  inactive: 'inactive',  //name of the class to be added when the cuepoint is inactive
  className: 'vjs-cuepoint', //sets a custom class for the visual cuepoint, by default is set to 'vjs-cuepoint'
  label: false,  //adds a text label to the cuepoint's visual. by default is shown on mose hover
  visual: false, // false, true or domElement
  width: null, //when set to true it will make the visual to occupy all the space between start and end on the timeline. Make sure to override the default css styling of the cuepoint or set the className of the cuepoint to something different than 'vjs-cuepoint' and write your own visual cuepoint css styles
});

//Cuepoints methods

myPlayer.cuepoints.add(); // add and return a cuepoint

myPlayer.cuepoints.wrapper(domElement); // set the cuepoints visual's wrapper dom element. When domElement not set it returns the current wrapper;

myPlayer.cuepoints.show(); // show all the markers that have a visual representation on the player's timeline

myPlayer.cuepoints.hide(); // hide all the markers that have a visual representation on the player's timeline

myPlayer.cuepoints.suspend(); // suspend all marker's actions

myPlayer.cuepoints.resume(); // resume all marker's actions

myPlayer.cuepoints.destroy(); // removes all the cuepoints

``` 

##### Responsive
Make a domElement to scale to the video's size and coordinates
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'));
myPlayer.responsive(el,{
  x: null,
  y: null,
  width: null,
  height: null,
  offsetX: 0,
  offsetY: 0,
  active: true, // set window.onResize calling
  onVisible: false, // resize the element only when visible
  scale : { //set to true or false what you wish to be scaled to the video's postion and size
      x: true,
      y: true,
      width: true,
      height: true
  },
  font : {
      min: false,
      ratio: false,
      lineHeight: null,
      units: "em"
  },
  callback: null, // callback function triggered onResize, recieves player's dimensions as param
});
```
When making an 'el' responsive using this plugin you have access to new methods that can be directly called with the element
``` javascript
el.responsive.update(o); // o = object with new parameters, see myPlayer.responsive(el, ...) up to view all available parameters,
el.responsive.resize(); // scale the el without waiting for window.onResize event;
el.responsive.disable(); // disable the automatic scaling of the element on video dimension/coordinates change
el.responsive.enable();  // enable the automatic scaling of the element on video dimension/coordinates change
```
##### Subtitles
Add/change the subtitle of a video
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'));
myPlayer.subtitle(src, options);
/*
  src: path to the subtitle text file
  options: {
    font:{
      min: 1, // set the subtitle's text minimum size
      ratio: 2, // set the subtitle's text size ratio increase
    },
    offset: 0, //set the Y offset of the subtitle
    autoHide: true //make subtitles wrapper respond to userinactive/useractive timeline's position
  }
*/
```
You can set as a parameter an array of obects when ajax cannot be called.
``` javascript
var src = [{start:0,end:0,text:'Lorem ipsum dolor'}, ...];
myPlayer.subtitle(src);
```
To unload/clear a subtitle call the plugin with no parameters
``` javascript
myPlayer.subtitle(src);
```

##### Bounds
Returns the video domElement bounds
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'));
var settings = {
  width: 1280,
  height: 720
}// optional
var data = myPlayer.bounds(settings);
data = {
  width: videoActualWidth, // the actual width of the video
  height: videoActualHeight, // the actual height of the video
  offset_x: bandW,  // the left and right offset size of the video (vertical black bars)
  offset_y: bandH,  // the top and bottom offset size of the video (horizontal black bars)
  width_org: videoWidth, // the original width of the video before scaling
  height_org: videoHeight, // the original height of the video before scaling
}
```
Call this plugin after the loadedmetada event of the player is triggered or set the video size manually. When the video size is set automatically it will affect the following pluings: responsive, overlays, subtitle. Best practice when not knowing the video original size and you don't want to depent on the loadedmetada event
##### Visibility
Make the video pause/play when not not focused/focused. Eg: Change tabs in browser.
``` javascript
 // can be directly set on the player initialization
var myPlayer = kmlplayer(document.querySelector('video'),{
  visibility: {
    onHidden: function() {},
    onVisible: function() {}
  }
  });

// or updated/added by calling directly the plugin
myPlayer.visibility({
  onHidden: function(){},
  onVisible: function() {}
});

```
##### Context menu
To be added
##### Powered by
To be added
##### Utils
Available general tools for easing the work.
``` javascript
var myPlayer = kmlplayer(document.querySelector('video'));

// To shorten load times, you should always offer the .mp3 as a last alternative.
myPlayer.utils.preloader.addFiles('file1', 'mysound*:sound.ogg||sound.mp3'); 

//for more details see https://github.com/jussi-kalliokoski/html5Preloader.js;

myPlayer.utils.device.ie(); // check if the player runs in Internet Explorer, returns false or browser version
myPlayer.utils.device.ios(); // check if the player runs on ipad/iphone

myPlayer.utils.url.params(); //returns url parameters
myPlayer.utils.hasClass(el, "className"); //check if el has a class
myPlayer.utils.addClass(el, "className"); //add class to el
myPlayer.utils.removeClass(el, "className"); //remove class from el
myPlayer.utils.toggleClass(el, "className"); //toggle class for el

```

#### Demos
To be added

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
[docs-image]:https://img.shields.io/badge/docs-45%25-orange.svg?style=flat-square
[license-image]:https://img.shields.io/badge/license-GPL-blue.svg?style=flat-square
[license-url]:LICENSE
[download-image]:https://img.shields.io/badge/download-1.0.0-yellowgreen.svg?style=flat-square
[download-url]:https://github.com/lmihaidaniel/kmlplayer/archive/master.zip