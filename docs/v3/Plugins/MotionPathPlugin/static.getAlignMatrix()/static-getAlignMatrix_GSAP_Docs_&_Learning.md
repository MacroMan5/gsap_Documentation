# static-getAlignMatrix | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getAlignMatrix()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getAlignMatrix())  
**Last Updated:** 2025-05-23T00:31:22.145Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-getAlignMatrix | GSAP | Docs & Learning

## MotionPathPlugin.getAlignMatrix

### MotionPathPlugin.getAlignMatrix( fromElement:Element | window, toElement:Element | window, fromOrigin:Array, toOrigin:Array | String ) : Matrix2D

Gets a Matrix2D for translating between coordinate spaces, typically so that you can move the `fromElement` to align it with the `toElement` while factoring in all transforms (even nested ones). The matrix allows you to convert any point/coordinate using its apply() method.

#### Parameters

*   #### **fromElement**: Element | window
    
    The element that serves as the basis for the alignment matrix. Typically this is the element that will be moved to the `toElement` using the resulting matrix.
    
*   #### **toElement**: Element | window
    
    The element that the `fromElement` should be aligned with
    
*   #### **fromOrigin**: Array
    
    \[optional\] Determines the point on the `fromElement` that gets aligned. It can be either an Array with progress values along the x and y axis like `[0.5, 0.5]` (center), `[1, 0]` (top right corner), etc. OR a point Object with pixel-based local coordinates like `{x: 100, y: 0}`
    
*   #### **toOrigin**: Array | String
    
    \[optional\] Determines the point on the `toElement` that gets aligned. It can be either an Array with progress values along the x and y axis like `[0.5, 0.5]` (center), `[1, 0]` (top right corner), etc. OR a point Object with pixel-based local coordinates like `{x: 100, y: 0}` OR for If the toElement is a <path> you can use `"auto"` to align with the beginning of the path itself rather than using the bounding box.
    

Gets a Matrix2D for translating between coordinate spaces, typically so that you can move the `fromElement` to align it with the `toElement` while factoring in all transforms (even nested ones). The matrix allows you to convert any point/coordinate using its `apply()` method. For example, you can get a matrix that aligns the top left corner of #div1 with the top left corner of #div2 (regardless of nested transforms) and then to plot where 200px over and 100px down (in #div2's coordinate space) corresponds to #div1's coordinates, you could `matrix.apply({x:200, y:100})`.

A Matrix2D is just an object with `a`, `b`, `c`, `d`, `e`, and `f` properties representing a 2D transformation matrix (very similar to an [SVGMatrix](https://developer.mozilla.org/en-US/docs/Web/API/SVGMatrix)). It contains all rotation, scale, skew, and x/y translation data and it's useful for converting between coordinate spaces. It has an `apply()` method that accepts a point (like `matrix.apply({x:0, y:100})`) and returns a new point with the matrix transforms applied.

```
// get a matrix for aligning the center of the dot element with the top left corner of the dragme element (which will be treated as 0,0)let matrix = MotionPathPlugin.getAlignMatrix(dot, dragme, [0.5, 0.5], [0, 0]),  // 0,0 is the origin of the alignment (the top left corner in this case), but try any local coordinates.  dragmePoint = { x: 0, y: 0 },  // convert into the dot's coordinate space (technically its parentNode's)  dotPoint = matrix.apply(dragmePoint);gsap.to(dot, {  // if there were already transforms applied, those would affect the matrix, so we should treat them as relative.  x: "+=" + dotPoint.x,  y: "+=" + dotPoint.y,  ease: "power1.inOut",});
```

#### loading...

  CodePen Embed - GSAP MotionPathPlugin.getAlignMatrix() Demo  

```
<h1>getAlignMatrix()</h1>
<p>Drag either box. When released, the green dot will animate (inside its container) to the center of the "Drag me" &lt;div&gt; using getAlignMatrix() to calculate the position even though both elements are scaled/rotated! The dot is nested inside a transformed container, so its coordinate system is distorted. No problem! Read the code comments for details.</p><br>
<div id="dragme">Drag me</div>
<div id="dot-container">
  Dot container
  <div id="dot"></div>
</div>








<a href="https://greensock.com"><img class="gsap-3-logo" src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/gsap-3-logo.svg" width="150" /></a>
```

```
body {
  padding: 10px 15px;
  text-align: center;
  overflow: hidden;
  background-color: #111;
  color: #aaa;
}

p {
  font-weight: 300;
  max-width: 900px;
  display: inline-block;
  text-align: left;
}

#dot-container {
  border: 2px solid #999;
  width: 160px;
  height: 70px;
  position: absolute;
  top: 0;
  left: 0;
  font-size: 22px;
  line-height: 35px;
  color: #ddd;
}

#dot,
#dragme::after  {
  position: absolute;
  top: 36px;
  left: 70px;
  border-radius: 50%;
  width: 20px;
  height: 20px;
  background-color: #88ce02;
}

#dragme {
  width: 200px;
  height: 140px;
  background-color: #555;
  color: white;
  text-align: center;
  line-height: 62px;
  font-size: 38px;
  display: inline-block;
  border: 2px solid #ccc;
}

.gsap-3-logo {
    width: 20vw;
    max-width: 150px;
    position: fixed;
    bottom: 15px;
    right: 15px;
}

#dragme::after { 
  content: '';
  top: calc(50% - 10px);
  left: calc(50% - 10px);
  background-color: black;
}
```

```
gsap.registerPlugin(Draggable, MotionPathPlugin);

let dragme = document.querySelector("#dragme"),
    dot = document.querySelector("#dot"),
    dotContainer = document.querySelector("#dot-container");

// apply some transforms to make it more impressive
gsap.to(dragme, {scale: 0.7, rotation: -20, y: 10, duration: 1.5});
gsap.to(dotContainer, {scale: 0.6, rotation: 25, y: 10, x: -10, duration: 1.5, delay: 1})

// make it draggable
Draggable.create([dragme, dotContainer], {onRelease: moveDot, bounds: window});

// here is where the magic is...
function moveDot() {
    let matrix = MotionPathPlugin.getAlignMatrix(dot, dragme, [0.5, 0.5], [0.5, 0.5]),
        // 0,0 is the origin of the alignment (the center in this case), but try any local coordinates like {x: 100, y: 70} for the bottom right corner.
        dragmePoint = {x: 0, y: 0}, 
        // convert the point into the dot's coordinate space (technically its parentNode's)
        dotPoint = matrix.apply(dragmePoint);
    
    gsap.to(dot, {
      // if there were already transforms applied, those would affect the matrix, so we should treat them as relative.
      x: "+=" + dotPoint.x, 
      y: "+=" + dotPoint.y,
      ease: "power1.inOut",
      overwrite: true
    });
}

gsap.delayedCall(2, () => {
  window.addEventListener("resize", () => {
    // wait 0.5 seconds after the last "resize" event fires (performance improvement) 
    gsap.killTweensOf(moveDot);
    gsap.delayedCall(0.5, moveDot);
  });
})
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
