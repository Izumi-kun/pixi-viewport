# pixi-viewport
A highly configurable viewport/2D camera designed to work with pixi.js.

Features include dragging, pinch-to-zoom, mouse wheel zooming, decelerated dragging, follow target, snap to point, snap to zoom, clamping, bouncing on edges, and move on mouse edges. See live example to try out all of these features.

All features are configurable and removable, so set up the viewport to be exactly what you need.

## Rationale
I kept rewriting 2d cameras for the games I developed with pixi.js, so I decided to package up a generic one. I included options that I need in my games, including edges that bounce, deceleration, and lots of options to tweak the feel of the viewport. 

## Simple Example
```js
var PIXI = require('pixi.js');
var Viewport = require('pixi-viewport');

var app = new PIXI.Application();
document.body.appendChild(app.view);

// create viewport
var viewport = new Viewport({
    screenWidth: window.innerWidth,
    screenHeight: window.innerHeight,
    worldWidth: 1000,
    worldHeight: 1000,

    interaction: app.renderer.interaction // the interaction module is important for wheel() to work properly when renderer.view is placed or scaled
});

// add the viewport to the stage
app.stage.addChild(viewport);

// activate plugins
viewport
    .drag()
    .pinch()
    .wheel()
    .decelerate();

// add a red box
var sprite = viewport.addChild(new PIXI.Sprite(PIXI.Texture.WHITE));
sprite.tint = 0xff0000;
sprite.width = sprite.height = 100
sprite.position.set(100, 100);
```

## Live Example
[https://davidfig.github.io/pixi-viewport/](https://davidfig.github.io/pixi-viewport/)

## API Documentation
[https://davidfig.github.io/pixi-viewport/jsdoc/](https://davidfig.github.io/pixi-viewport/jsdoc/)

## Installation

    npm i pixi-viewport

or [grab the latest release](https://github.com/davidfig/pixi-viewport/releases/) and use it:

```html
<script src="/directory-to-file/pixi.js"></script>
<script src="/directory-to-file/pixi-viewport.js"></script>
<script>
    var Viewport = new PIXI.extras.Viewport(options);
</script>
```

## Other Libraries
If you liked pixi-viewport, please try my other open source libraries:
* [pixi-scrollbox](https://github.com/davidfig/pixi-scrollbox) - pixi.js scrollbox: a masked box that can scroll vertically or horizontally with scrollbars (uses pixi-viewport)
* [pixi-ease](https://github.com/davidfig/pixi-ease) - pixi.js animation library using easing functions
* [intersects](https://github.com/davidfig/intersects) - a simple collection of 2d collision/intersects functions. Supports points, circles, lines, axis-aligned boxes, and polygons

## license  
MIT License  
(c) 2018 [YOPEY YOPEY LLC](https://yopeyopey.com/) by [David Figatner](https://twitter.com/yopey_yopey/)
