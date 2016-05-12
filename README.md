<img src="http://player.kumullus.com/assets/logo.svg" width="15%">

## HTML VIDEO PLAYER

![Build Status][version-image]
![Docs Status][docs-image]
[![MIT License][license-image]][license-url]
[![Download][download-image]][download-url]

> A complete HTML/CSS video player built on top of [video.js](https://github.com/videojs/video.js).
>
> It aims to bring and sync interactive elements on top of the video.

- [Installation and configuration](#installation-and-configuration)
- [Usage](#usage)
- [Plugins](#plugins)
- [Demos](#demos)
- [F.A.Q](#frequently-asked-questions)
- [License](#license)
- [Credits and Acknowledgments](#credits-and-acknowledgments)

#### Installation and configuration

__1. Download the package__

Download the [kmlPlayer](https://github.com/lmihaidaniel/kmlplayer/archive/master.zip) package and move it in your assets folder.

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

#### Usage

#### Plugins

- [Overlays](#overlay)
- [Cuepoints](#cuepoint)
- [Responsive](#responsive)
- [Subtitles](#subtitles)
- [Bounds](#bounds)
- [Visibility](#visibility)
- [utils](#utils)
- [SCORM](#scorm)
- [Context menu](#contextmenu)
- [Powered by](#poweredBy)


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
[docs-image]:https://img.shields.io/badge/docs-50%25-orange.svg?style=flat-square
[license-image]:https://img.shields.io/badge/license-GNU-blue.svg?style=flat-square
[license-url]:LICENSE
[download-image]:https://img.shields.io/badge/download-1.0.0-yellowgreen.svg?style=flat-square
[download-url]:http://player.kumullus.com/download