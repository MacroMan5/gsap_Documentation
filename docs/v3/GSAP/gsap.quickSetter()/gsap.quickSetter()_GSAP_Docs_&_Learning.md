# gsap.quickSetter() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.quickSetter()](https://gsap.com/docs/v3/GSAP/gsap.quickSetter())  
**Last Updated:** 2025-05-23T00:22:18.920Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.quickSetter() | GSAP | Docs & Learning

### Returns : Function[​](#returns--function "Direct link to Returns : Function")

### Details[​](#details "Direct link to Details")

If you find yourself calling `gsap.set()` many times on the same object (or set of objects), like in a "mousemove" event, you can **boost performance 50% - 250%** by creating a quickSetter function and using that instead of `gsap.set()`. Think of a quickSetter like an optimized function tied to a particular target's (or set of targets') property, where it directly pipes data to it and **skips** convenience tasks in a normal `gsap.set()` call such as:

*   Unit conversion and auto-appending of units (though you can specify a unit for the quickSetter that'll always get appended to the number you feed in)
*   Relative values
*   Function-based values
*   `"random()"` parsing
*   Special workarounds for property-specific browser inconsistencies like transformOrigin on SVG elements (so it isn't advisable to create a quickSetter for transformOrigin).
*   Property name alias conversion ("x" will work for transforms, but "translateX" won't)

note

Don't be afraid to use `gsap.set()` because in most cases you'd never notice a real-world performance difference by switching to a quickSetter and `gsap.set()` provides a lot of worthwhile conveniences. But at GreenSock we're performance nuts, so we wanted to provide a tool for hyper-optimized property setting in performance-critical cases where you've got a **LOT** updates going on.

## Combine with utility methods for super-powerful functions![​](#combine-with-utility-methods-for-super-powerful-functions "Direct link to Combine with utility methods for super-powerful functions!")

Since it accepts a single value, you can slap a quickSetter at the end of a [`pipe()`](https://gsap.com/docs/v3/GSAP/UtilityMethods/pipe\(\)), after other utility functions that do useful things to the numbers you feed in, like [clamping](https://gsap.com/docs/v3/GSAP/UtilityMethods/clamp\(\)) or [snapping](https://gsap.com/docs/v3/GSAP/UtilityMethods/snap\(\)) or somehow sanitizing the values. For example:

```
let xSetter = gsap.utils.pipe(    gsap.utils.clamp(0, 100),    //make sure the number is between 0 and 100    gsap.utils.snap(5),          //snap to the closest increment of 5    gsap.quickSetter("#id", "x", "px") //apply it to the #id element's x property and append a "px" unit  );//then later...xSetter(150) //sets the #el's transform to translateX(100px) (clamped to 100)xSetter(3)   //sets it to 5px (snapped)...
```

## Mouse Follower Demo[​](#mouse-follower-demo "Direct link to Mouse Follower Demo")

#### loading...

  CodePen Embed - mouse follower demo - optimised  

```
<div class="flair flair--3"></div>
```

```
h1 {
  margin: 1rem;
  text-align: center;
}
.flair {
  width: 100px;
  height: 100px;
  position: fixed;
  top: 0;
  left: 0;
  pointer-events: none;
}
```

```
gsap.set(".flair", {xPercent: -50, yPercent: -50});

let xSetter = gsap.quickSetter(".flair", "x", "px") //apply it to the #id element's x property and append a "px" unit
let ySetter = gsap.quickSetter(".flair", "y", "px") //apply it to the #id element's x property and append a "px" unit

window.addEventListener("mousemove", e => {  
  xSetter(e.x)
  ySetter(e.y)
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

## If you're animating, use gsap.quickTo()[​](#if-youre-animating-use-gsapquickto "Direct link to If you're animating, use gsap.quickTo()")

gsap.quickSetter() is aimed at immediately setting values, but if you'd prefer to **animate** to new values instead, check out the [gsap.quickTo()](https://gsap.com/docs/v3/GSAP/gsap.quickTo\(\)) method instead. Here's a mouse follower demo using that:

#### loading...

  CodePen Embed - gsap.quickTo() mouse follower (GSAP 3)  

```
<div class="flair flair--3"></div>
```

```
.flair {
  width: 100px;
  height: 100px;
  position: fixed;
  top: 0;
  left: 0;
  pointer-events: none;
}
```

```
// requires GSAP 3.10.0 or later
// older quickSetter version: https://codepen.io/GreenSock/pen/WNNNBpo

gsap.set(".flair", {xPercent: -50, yPercent: -50});

let xTo = gsap.quickTo(".flair", "x", {duration: 0.6, ease: "power3"}),
    yTo = gsap.quickTo(".flair", "y", {duration: 0.6, ease: "power3"});

window.addEventListener("mousemove", e => {
  xTo(e.clientX);
  yTo(e.clientY);
});




// 💚 This just adds the GSAP link to this pen, don't copy this bit
import { GSAPInfoBar } from "https://codepen.io/GreenSock/pen/vYqpyLg.js"
new GSAPInfoBar({ link: "https://gsap.com/docs/v3/GSAP/gsap.quickTo()/" });
// 💚 Happy tweening!
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

### Trick for multiple values[​](#trick-for-multiple-values "Direct link to Trick for multiple values")

You can get the benefits of CSSPlugin (like relative values, `"random()"` parsing, etc.) and the ability to apply **multiple** properties to DOM elements by setting the `property` of the quickSetter to **"css"** and then passing in the value as an _object_, like:

```
var boxSet = gsap.quickSetter("#box", "css");boxSet({ x: "+=100", y: "random(-100, 100)" }); //works!
```

This technique also works for attributes (using "attr" instead):

```
var circleSet = gsap.quickSetter("#circle", "attr");circleSet({ cx: "+=100", cy: "random(-100, 100)" }); //works!
```

But this won't deliver as much of a performance boost as you'd get by using a specific property like `gsap.quickSetter("#box", "x", "px")`. It's still faster than a standard gsap.set(), though.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
