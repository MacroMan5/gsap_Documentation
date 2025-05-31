# static-getRelativePosition | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getRelativePosition()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getRelativePosition())  
**Last Updated:** 2025-05-23T00:31:37.019Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-getRelativePosition | GSAP | Docs & Learning

## MotionPathPlugin.getRelativePosition

### MotionPathPlugin.getRelativePosition( fromElement:Element | window, toElement:Element | window, fromOrigin:Array | Object, toOrigin:Array | Object | String ) : Object

Gets the x and y distances between two elements regardless of nested transforms! feed two elements to this method and it'll return the gap between them as a point {x, y} according to the coordinate system of the fromElement's parent.

#### Parameters

*   #### **fromElement**: Element | window
    
    The element from which the distance is measured (typically this is the element that will be moved to the `toElement`)
    
*   #### **toElement**: Element | window
    
    The destination element. This should be an element reference (like myElem), not a selector string (like "#myElem").
    
*   #### **fromOrigin**: Array | Object
    
    \[optional\] Determines the point on the `fromElement` that serves as the origin of the measurements. It can be either an Array with progress values along the x and y axis like `[0.5, 0.5]` (center), `[1, 0]` (top right corner), etc. OR a point Object with pixel-based local coordinates like `{x: 100, y: 0}`
    
*   #### **toOrigin**: Array | Object | String
    
    \[optional\] Determines the point on the `toElement` to which to measure. It can be either an Array with progress values along the x and y axis like `[0.5, 0.5]` (center), `[1, 0]` (top right corner), etc. OR a point Object with pixel-based local coordinates like `{x: 100, y: 0}` OR for If the toElement is a <path> you can use `"auto"` to align with the beginning of the path itself rather than using the bounding box.
    

Gets the x and y distances between two elements regardless of nested transforms! feed two elements to this method and it'll return the gap between them as a point {x, y} according to the coordinate system of the fromElement's parent. By default, it will align their top left corners (bounding box), but you can define a different origin for each, like `[0.5,&#xA0;0.5]` would be the center, `[1,&#xA0;1]` would be the bottom right, etc.

```
let inner = document.querySelector("#inner"),  dot = document.querySelector("#dot"),  delta = MotionPathPlugin.getRelativePosition(    dot,    inner,    [0.5, 0.5],    [0.5, 0.5]  );gsap.to(dot, {  x: "+=" + delta.x,  y: "+=" + delta.y,  duration: 2,  ease: "power2.inOut",});
```

#### loading...

  CodePen Embed - getRelativePosition() Demo  

```
<h1>GSAP 3 getRelativePosition() Demo</h1><div id="outer">
  <div id="middle">
    <div id="inner"></div>
  </div>
</div>
<div id="dot-container">
  <div id="dot"></div>
</div>

<link href='//fonts.googleapis.com/css?family=Signika+Negative:300,400' rel='stylesheet' type='text/css'>
```

```
body {
  background-color: black;
  color: white;
  font-family: "Signika Negative", Arial, sans-serif;
  font-weight: 300;
  padding: 5px 15px;
}
#dot {
  position: absolute;
  top: 0;
  left: 0;
  width: 16px;
  height: 16px;
  background-color: red;
  border-radius: 50%;
}
#dot-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100px;
  height: 50px;
  border: 2px solid green;

}
#outer {
  width: 500px;
  height: 350px;
  background-color: #444;
}
#middle {
  width: 300px;
  height: 200px;
  background-color: #656565;
}
#inner {
  width: 100px;
  height: 60px;
  background-color: #ccc;
}
```

```
// The red dot goes to the center of the light rectangle even though it's nested inside multiple elements with various transforms applied!

// First, let's add some wacky transforms to every element (nested!)
var tl = gsap.timeline({defaults: {duration:1, delay:0.5, ease: "power1.inOut"}})
  .to("#outer", {xPercent: 50, yPercent: 20, rotation: -20, y: -80})
  .to("#middle", {x: 100, y: 50, scale: 0.7, rotation: 60})
  .to("#inner", {x: 140, y: 100, transformOrigin: "50% 50%", rotation: 40})
  .to("#dot-container", {x:50, y:80, scale:0.5, rotation:-25})
  .call(function() {
    // RED DOT MOVEMENT:
    var inner = document.querySelector("#inner"),
        dot = document.querySelector("#dot"),
        delta = MotionPathPlugin.getRelativePosition(dot, inner, [0.5, 0.5], [0.5, 0.5]);
    gsap.to(dot, {
      x: "+=" + delta.x,
      y: "+=" + delta.y,
      duration: 2,
      delay: 1,
      repeat: -1,
      yoyo: true,
      repeatDelay:1,
      ease: "power2.inOut"
    });
  });

```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

You can also localize the pointer coordinates, like in the below demo (click anywhere)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
