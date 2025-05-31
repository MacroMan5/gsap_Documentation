# static-track | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/InertiaPlugin/static.track()](https://gsap.com/docs/v3/Plugins/InertiaPlugin/static.track())  
**Last Updated:** 2025-05-23T00:30:42.227Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-track | GSAP | Docs & Learning

## InertiaPlugin.track

### InertiaPlugin.track( target:Element | String | Array, props:String ) : Array

#### Parameters

*   #### **target**: Element | String | Array
    
    The Element(s) that should be tracked. This can be selector text, an Element, or an Array of Elements.
    
*   #### **props**: String
    
    A comma-delimited list of property names to track, like `"x"` or `"x,y,rotation"`
    

### Returns : Array[​](#returns--array "Direct link to Returns : Array")

An Array of VelocityTracker objects (one for each target object). The most useful method is its `get()` method that you feed the property name to like `myTracker.get("y")` to get the target's current `y` `velocity`. Normally, however, you don't need to keep track of this VelocityTracker object at all because the work is done internally and InertiaPlugin knows how to find it.

### Details[​](#details "Direct link to Details")

Tracks the velocity of any property (or comma-delimited list of properties) of a particular object so that you can do any of the following:

*   Create an `inertia` tween with `velocity: "auto"`, which tells InertiaPlugin to automatically find the associated tracker and grab the velocity from there without you needing to feed in a certain number/velocity.
*   If you need the current velocity of a tracked property anytime for some other reason, it's easy. `InertiaPlugin.getVelocity(target, "property");`

To start tracking, just feed in the target (which can be selector text or an Array of objects) along with a comma-delimited list of properties that you want tracked like this:

```
InertiaPlugin.track(obj, "x,y");// or selector text which could find multiple targets:InertiaPlugin.track(".class", "x,y");
```

Then every time the GSAP updates, the tracked properties will be recorded along with time stamps (it keeps a maximum of 2 of these values and continually writes over the previous ones, so don't worry about memory buildup). This even works with function-based properties like getters and setters!

Then, after at least 100ms and 2 “ticks” (frames) have elapsed (so that some data has been recorded), you can create `inertia` tweens for those properties and omit the `velocity` values and it will automatically populate them for you internally. For example:

```
//first, start tracking "x" and "y":InertiaPlugin.track(obj, "x,y");//then, after at least 100ms, let's smoothly tween to EXACTLY x:200, y:300gsap.to(obj, {  inertia: {    x: { end: 200 },    y: { end: 300 },  },});//and if you want things to use the defaults and have obj.x and obj.y glide to a stop based on the velocity rather than setting any destination values, just use "auto":gsap.to(obj, {  inertia: {    x: "auto",    y: "auto",  },});
```

Here's an example of tracking in use:

#### loading...

  CodePen Embed - Draggable Bounce  

```
body {
  overflow: hidden;
}

.ball {
  width: 125px;
  height: 125px;
  background: #2196F3;
  border-radius: 50%;
  border: 3px solid #1565c0;
  box-sizing: border-box;
  will-change: transform;
  position: absolute;
}
```

[View Compiled](#0)

```
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

[![](https://assets.codepen.io/t-1/user-default-avatar.jpg?fit=crop&format=auto&height=256&version=0&width=256)](https://codepen.io/osublake)

So `"auto"` is a valid option for properties you're tracking.

## What kinds of properties can be tracked?[​](#what-kinds-of-properties-can-be-tracked "Direct link to What kinds of properties can be tracked?")

Pretty much any numeric property of any object can be tracked, including function-based ones. For example, `obj.x` or `obj.rotation` or even `obj.customProp()`. You cannot, however, track custom plugin-related values like `scrollTo`, `autoAlpha`, or `physics2D` because those aren't real properties of the object. You should instead track the real properties that those plugins affect, like `rotation`, `opacity`, `x`, or `y`.

Important

It is best to `untrack()` properties when you're done tracking them in order to maximize performance and ensure things are released for garbage collection. To untrack, simply use the [`untrack()`](https://gsap.com/docs/v3/Plugins/InertiaPlugin/static.untrack\(\)) method.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
