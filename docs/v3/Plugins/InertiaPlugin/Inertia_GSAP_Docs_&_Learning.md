# Inertia | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/InertiaPlugin/](https://gsap.com/docs/v3/Plugins/InertiaPlugin/)  
**Last Updated:** 2025-05-23T00:18:14.724Z  
**Extracted:** 2025-05-31 16:56:03

---

# Inertia | GSAP | Docs & Learning

Quick Start

#### CDN Link

```
gsap.registerPlugin(InertiaPlugin) 
```

#### Minimal usage

```
gsap.to(obj, { inertia: { x: 500, y: -300 } });
```

## Description[​](#description "Direct link to Description")

InertiaPlugin (formerly ThrowPropsPlugin) allows you to smoothly glide any property to a stop, honoring an initial velocity as well as applying optional restrictions on the end value. You can define a specific end value or allow it to be chosen automatically based on the initial velocity (and ease) or you can define a max/min range or even an array of snap-to values that act as notches. You can have it "watch" certain properties to keep track of their velocities and then use them automatically when you do an `inertia` tween. This is perfect for flick-scrolling or animating things as though they are being thrown (where momentum factors into the animation).

For example, let's say a user drags a ball and and then when released, the ball should continue flying at the same velocity as it was just moving (so that it appears seamless), and then glide to a rest. You can't do a normal tween because you don't know exactly where it should land or how long the tween should last (faster initial velocity would usually mean a longer duration). You'd like it to decelerate based on whatever ease you define in your tween.

Maybe you want the final resting value to always land within a particular range so that the ball doesn't fly off the edge of the screen. But you don't want it to suddenly jerk to a stop when it hits the edge of the screen either; instead, you want it to ease gently into place even if that means going past the landing spot briefly and easing back (if the initial velocity is fast enough to require that). The whole point is to make it look **smooth**.

**No problem.**

In its simplest form, you can pass just the initial velocity for each property like this:

```
gsap.to(obj, { inertia: { x: 500, y: -300 } });
```

In the above example, `obj.x` will animate at 500 pixels per second initially and `obj.y` will animate at -300 pixels per second. Both will decelerate smoothly until they come to rest and InertiaPlugin figures out a natural-looking duration for you!

To impose maximum and minimum boundaries on the end values, use the object syntax with the `max` and `min` special properties like this:

```
gsap.to(obj, {  inertia: {    x: {      velocity: 500,      max: 1024,      min: 0,    },    y: {      velocity: -300,      max: 720,      min: 0,    },  },});
```

Notice the nesting of the objects (`{}`). The `max` and `min` values refer to the range for the final resting position (coordinates in this case), **not** the velocity. So `obj.x` would always land between 0 and 1024 in this case, and `obj.y` would always land between 0 and 720. If you want the target object to land on a specific value rather than within a range, simply set `max` and `min` to identical values or just use the `end` property. Also notice that you must define a `velocity` value for each property (unless you're using `track()` - see below for details).

## Config Object[​](#config-object "Direct link to Config Object")

*   #### velocity[](#velocity)
    
    \[_Number_ | _“auto”_\] - The initial velocity, measured in units per second. You may omit velocity or just use “auto” for properties that are being tracked automatically using the track() method.
    
*   #### min[](#min)
    
    Number - The minimum end value of the property. For example, if you don’t want `x` to land at a value below 0, your `inertia` may look like `{x: {velocity: -500, min: 0}}`.
    
*   #### max[](#max)
    
    Number - The maximum end value of the property. For example, if you don’t want `x` to exceed 1024, your `inertia` may look like `{x: {velocity: 500, max: 1024}}`.
    
*   #### end[](#end)
    
    \[_Number_ | _Array_ | _Function_\] - If `end` is defined as a **Number**, the target will land EXACTLY there (just as if you set both the `max` and `min` to identical values). If `end` is defined as a numeric **Array**, those values will be treated like “notches” or “snap-to” values so that the closest one to the natural landing spot will be selected. For example, if `[0,100,200]` is used, and the value would have naturally landed at 141, it will use the closest number (100 in this case) and land there instead. If end is defined as a **Function**, that function will be called and passed the natural landing value as the only parameter, and your function can run whatever logic you want, and then return the number at which it should land. This can be useful if, for example, you have a rotational tween and you want it to snap to 10-degree increments no matter how big or small, you could use a function that just rounds the natural value to the closest 10-degree increment. So any of these are valid: `end: 100`, `end: [0,100,200,300]`, or `end: function(n) { return Math.round(n / 10) * 10; }`.
    
*   #### linkedProps[](#linkedProps)
    
    String - A comma-delimited list of properties that should be linked together into a single object when passed to a function-based `end` value so that they’re processed together. This is only useful when, for example, you have an `x` and `y` but the logic in your end function needs BOTH of those (like for snapping coordinates). See [this demo](https://codepen.io/GreenSock/pen/aqEdGM?editors=0010) for an example. The object that gets passed as the only parameter to the `end` function will have the properties are listed in `linkedProps`. So, for example, if `linkedProps` is `"x,y"`, then an object like `{x: 100, y: 140}` gets passed to the function as a parameter. Those values are the natural ending values, but of course your function should return a similar object with the new values you want the end values to be, like `return {x: 200, y: 300}`.
    
*   #### resistance[](#resistance)
    
    Number - The amount of resistance per second (think of it like how much friction is applied)..
    

InertiaPlugin isn't just for tweening x and y coordinates. It works with any numeric property, so you could use it for spinning the `rotation` of an object as well. Or the `scaleX`/`scaleY` properties. Maybe the user drags to spin a wheel and lets go and you want it to continue increasing the `rotation` at that velocity, decelerating smoothly until it stops. It even works with method-based getters/setters.

## Automatically determine duration[​](#automatically-determine-duration "Direct link to Automatically determine duration")

One of the trickiest parts of creating a `inertia` tween that looks fluid and natural (particularly if you're applying maximum and/or minimum values) is determining its duration. Typically it's best to have a relatively consistent level of resistance so that if the initial velocity is very fast, it takes longer for the object to come to rest compared to when the initial velocity is slower. You also may want to impose some restrictions on how long a tween can last (if the user drags incredibly fast, you might not want the tween to last 200 seconds). The duration will also affect how far past a max/min boundary the property may go, so you might want to only allow a certain amount of overshoot tolerance. That's why InertiaPlugin automatically sets the duration of the Tween for you, and you can optionally hard-code a duration in the inertia object or even use max/min values to give it a range, like `duration:{min:0.5, max:3}`.

## Automatically track velocity[​](#automatically-track-velocity "Direct link to Automatically track velocity")

Another tricky aspect of smoothly transitioning from a particular velocity is tracking the property's velocity in the first place! So we've made that easier too - you can use the [`InertiaPlugin.track()`](https://gsap.com/docs/v3/Plugins/InertiaPlugin/) method to have the velocity (rate of change) of certain properties tracked and then `inertia` tweens will automatically grab the appropriate tracked value internally, allowing you to omit the `velocity` values in your tweens altogether. See the [`track()`](https://gsap.com/docs/v3/Plugins/InertiaPlugin/static.track\(\)) method's description for details. And make sure you start tracking velocity at least a half-second before you need to tween because it takes a small amount of time to gauge how fast something is going.

A unique convenience of InertiaPlugin compared to most other solutions out there that use frame-based loops is that everything is reversible and you can jump to any spot in the tween immediately. So if you create several `inertia` tweens, for example, and dump them into a timeline, you could simply call `reverse()` on the timeline to watch the objects retrace their steps right back to the beginning!

## Examples[​](#examples "Direct link to Examples")

The following example creates a green box and a red box that you can drag and toss around the screen in a natural, fluid way. If you check the "Snap to grid" checkbox, the boxes will always land exactly on the grid. We use `Draggable` class so that we can focus more on the InertiaPlugin code rather than all the boilerplate code needed to make things draggable:

#### loading...

  CodePen Embed - Draggable Demo  

```
<div>
<div id="container">
    <div class="box gradient-green" id="box1"><p>Drag and throw me</p></div>
    <div class="box gradient-blue" id="box2" ><p>Drag and throw me too</p></div>
</div>
<div class="controls">
        <ul>
          <li class="controlsTitle">Options</li>
          <li>
            <label><input type="checkbox" name="snap" id="snap" value="1" /> Snap end position to grid</label>
          </li>
          <li>
            <label><input type="checkbox" name="liveSnap" id="liveSnap" value="1" /> Live snap</label>
          </li>
        </ul>
      </div>
</div>
```

```
html,
body {
  margin: 0;
  padding: 0;
  height: 100vh;
  overflow: hidden;
}
body {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}

#container {
  height: 801px;
  overflow: visible;
  padding: 0;
  position: relative;
}

.box {
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 196px;
  height: 100px;
  position: absolute;
  top: 0;
  border-radius: 10px;
}

.controls {
  border: 1px solid #555;
  font-size: 18px;
  margin: 20px 0;
}
.controls ul {
  list-style: none;
  padding: 0;
  margin: 0;
}
.controls li {
  display: inline-block;
  padding: 8px 0 8px 10px;
  margin: 0;
}
.controls input {
  vertical-align: middle;
  cursor: pointer;
}
.controls .controlsTitle {
  border-right: 1px solid #555;
  border-bottom: none;
  padding-right: 10px;
}
```

```
/*
See https://gsap.com/draggable/ for details. 
This demo uses InertiaPlugin which is a membership benefit of Club GreenSock, https://gsap.com/pricing/
*/
gsap.registerPlugin(InertiaPlugin);

var $snap = $("#snap"),
  $liveSnap = $("#liveSnap"),
  $container = $("#container"),
  gridWidth = $("body").width() / 5,
  gridHeight = 100,
  gridRows = 3,
  gridColumns = 5,
  i, x, y;

//loop through and create the grid (a div for each cell). Feel free to tweak the variables above
for (i = 0; i < gridRows * gridColumns; i++) {
  y = Math.floor(i / gridColumns) * gridHeight;
  x = (i * gridWidth) % (gridColumns * gridWidth);
  $("<div/>").css({position:"absolute", border:"1px solid #454545", width:gridWidth-1, height:gridHeight-1, top:y, left:x}).prependTo($container);
}

//set the container's size to match the grid, and ensure that the box widths/heights reflect the variables above
gsap.set($container, {height: gridRows * gridHeight + 1, width: gridColumns * gridWidth + 1});
gsap.set(".box", {width:gridWidth, height:gridHeight});
gsap.set("#box2", {left: gridWidth * 2})

//the update() function is what creates the Draggable according to the options selected (snapping).
function update() {
  var snap = $snap.prop("checked"),
      liveSnap = $liveSnap.prop("checked");
  Draggable.create(".box", {
    bounds: $container,
    edgeResistance: 0.65,
    type: "x,y",
    inertia: true,
    autoScroll: true,
    liveSnap: liveSnap,
    snap:{
      x: function(endValue) {
        return (snap || liveSnap) ? Math.round(endValue / gridWidth) * gridWidth : endValue;
      },
      y: function(endValue) {
        return (snap || liveSnap) ? Math.round(endValue / gridHeight) * gridHeight : endValue;
      }
    }
  });
}

//when the user toggles one of the "snap" modes, make the necessary updates...
$snap.on("change", applySnap);
$liveSnap.on("change", applySnap);

function applySnap() {
  if ($snap.prop("checked") || $liveSnap.prop("checked")) {
    $(".box").each(function(index, element) {
      gsap.to(element, {
        x: Math.round(gsap.getProperty(element, "x") / gridWidth) * gridWidth,
        y: Math.round(gsap.getProperty(element, "y") / gridHeight) * gridHeight,
        delay: 0.1,
        ease: "power2.inOut"
      });
    });
  }
  update();
}

update();
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

### External CSS

1.  [https://codepen.io/GreenSock/pen/xxmzBrw/fcaef74061bb7a76e5263dfc076c363e.css](https://codepen.io/GreenSock/pen/xxmzBrw/fcaef74061bb7a76e5263dfc076c363e.css)

### External JavaScript

1.  [//cdnjs.cloudflare.com/ajax/libs/jquery/2.1.3/jquery.min.js](https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.3/jquery.min.js)
2.  [https://cdn.jsdelivr.net/npm/gsap@3.1.0/dist/gsap.min.js](https://cdn.jsdelivr.net/npm/gsap@3.1.0/dist/gsap.min.js)
3.  [https://cdn.jsdelivr.net/npm/gsap@3.1.0/dist/Draggable.min.js](https://cdn.jsdelivr.net/npm/gsap@3.1.0/dist/Draggable.min.js)
4.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/InertiaPlugin.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/InertiaPlugin.min.js)

The following example demonstrates using a custom `end` function for complex snapping that requires both x and y values, thus `linkedProps` is used:

#### loading...

  CodePen Embed - Draggable 3 with snapping  

```
<!-- forked from <a href="https://codepen.io/osublake/">Blake Bowen.</a>
 -->
<svg id="svg" viewBox="0 0 400 400">

  <defs>
    <circle class="handle" r="10" />
    <circle class="marker" r="4" />  
    
    <linearGradient id="grad-1" x1="0" y1="0" x2="400" y2="400" gradientUnits="userSpaceOnUse">
       <stop offset="0.2" stop-color="#00bae2"></stop>
       <stop offset="0.8" stop-color="#fec5fb"></stop>
    </linearGradient>
  </defs>
  
  <polygon id="star" stroke="url(#grad-1)" points="261,220 298,335 200,264 102,335 139,220 42,149 162,148 200,34 238,148 358,149" />  
  <g id="marker-layer"></g>
  <g id="handle-layer"></g>
</svg>
```

```
body {
  background: #0e100f;
  font-family:sans-serif;
  color:#7c7c6f;
}

#svg {
  position: fixed;
  top: 10%;
  left: 10%;
  width: 80%;
  height: 80%;
  overflow: visible
}

#star {
  stroke-width: 20;
  stroke-linejoin: round;
  fill: none;
}

.handle {
  fill: transparent;
  stroke-width: 4;
  stroke: #fff;
}

.marker {
  fill: #fec5fb;
  stroke: #fec5fb;
  pointer-events: none;
}



a:link, a:visited, a:active {
  color:#7c7c6f;
  text-decoration:none;
}

a:hover {
  color:#00bae2;
}
```

```
//original by Blake Bowen https://codepen.io/osublake/
var star = document.querySelector("#star");
var markerDef = document.querySelector("defs .marker");
var handleDef = document.querySelector("defs .handle");
var markerLayer = document.querySelector("#marker-layer");
var handleLayer = document.querySelector("#handle-layer");

var points = [];
var numPoints = star.points.numberOfItems;

for (var i = 0; i < numPoints; i++) {  
  var point = star.points.getItem(i);
  points[i] = {x:point.x, y:point.y};
  createHandle(point);
}

function createHandle(point) {
    
  var marker = createClone(markerDef, markerLayer, point);
  var handle = createClone(handleDef, handleLayer, point);
  var update = function() { point.x = this.x; point.y = this.y; };
  
  var draggable = new Draggable(handle, {
    onDrag: update,
    onThrowUpdate: update,
    inertia: true,
    bounds: window,
    liveSnap:{
      points:points,
      radius:15
    }
  });
}

function createClone(node, parent, point) {
  var element = node.cloneNode(true);
  parent.appendChild(element);
  gsap.set(element, { x: point.x, y: point.y });
  return element;
}
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

Although InertiaPlugin is commonly used with Draggable, Draggable is not required an InertiaPlugin can be used independently from Draggable.. Here's an example of Inertia's tracking being used directly:

#### loading...

  CodePen Embed - Draggable bounce  

```
<img class="ball" src="https://assets.codepen.io/16327/circle.png" alt="" />
```

```
body {
  background: #0e100f;
  font-family:sans-serif;
  color:#7c7c6f;
  overflow: hidden;
}

.ball {
  width: 125px;
  height: 125px;
  border-radius: 50%;
  box-sizing: border-box;
  will-change: transform;
  position: absolute;
}
```

```
//original by Blake Bowen https://codepen.io/osublake/
console.clear();

const friction = -0.5;

const ball = document.querySelector(".ball");
const ballProps = gsap.getProperty(ball);
const radius = ball.getBoundingClientRect().width / 2;
const tracker = InertiaPlugin.track(ball, "x,y")[0];

let vw = window.innerWidth;
let vh = window.innerHeight;

gsap.defaults({
  overwrite: true
});

gsap.set(ball, {
  xPercent: -50,
  yPercent: -50,
  x: vw / 2,
  y: vh / 2
});

const draggable = new Draggable(ball, {
  bounds: window,
  onPress() {
    gsap.killTweensOf(ball);
    this.update();
  },
  onDragEnd: animateBounce,
  onDragEndParams: []
});

window.addEventListener("resize", () => {
  vw = window.innerWidth;
  vh = window.innerHeight;
});

function animateBounce(x = "+=0", y = "+=0", vx = "auto", vy = "auto") {
    
  gsap.fromTo(ball, { x, y }, {
    inertia: {
      x: vx,
      y: vy,
    },
    onUpdate: checkBounds
  });  
}

function checkBounds() {
  
  let r = radius;    
  let x = ballProps("x");
  let y = ballProps("y");
  let vx = tracker.get("x");
  let vy = tracker.get("y");
  let xPos = x;
  let yPos = y;

  let hitting = false;

  if (x + r > vw) {
    xPos = vw - r;
    vx *= friction;
    hitting = true;

  } else if (x - r < 0) {
    xPos = r;
    vx *= friction;
    hitting = true;
  }

  if (y + r > vh) {
    yPos = vh - r;
    vy *= friction;
    hitting = true;

  } else if (y - r < 0) {
    yPos = r;
    vy *= friction;
    hitting = true;
  }

  if (hitting) {
    animateBounce(xPos, yPos, vx, vy);
  } 
}
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

## **Methods**[​](#methods "Direct link to methods")

## **Demos**[​](#demos "Direct link to demos")

Inertia pairs great with Draggable - check out the Draggable [how-to collection](https://codepen.io/collection/AtuHb) and our favourite [inspiring community demos](https://codepen.io/collection/DrQGpM) on CodePen.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
