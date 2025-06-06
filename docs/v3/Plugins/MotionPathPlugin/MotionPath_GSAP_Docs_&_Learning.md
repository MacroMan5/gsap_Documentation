# MotionPath | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/MotionPathPlugin](https://gsap.com/docs/v3/Plugins/MotionPathPlugin)  
**Last Updated:** 2025-05-23T00:18:45.047Z  
**Extracted:** 2025-05-31 16:56:03

---

# MotionPath | GSAP | Docs & Learning

Quick Start

#### CDN Link

```
gsap.registerPlugin(MotionPathPlugin) 
```

#### Minimal usage

```
gsap.to("#div", {  motionPath: {    path: "#path",  },  transformOrigin: "50% 50%",  duration: 5,});
```

info

MotionPathPlugin by GreenSock - YouTube

Animate any object along a path (or even through arbitrary property values). The motionPath can be defined as any of the following:

*   An SVG **`<path>`** element (selector text or direct reference) like:
    
*   A **string of SVG path data** like:
    
    ```
    motionPath: "M9,100c0,0,18-41,49-65";
    ```
    
*   An **Array of objects with x,y coordinates**. By default, it will draw a curved path **through** these coordinates, but set `type: "cubic"` if they describe a cubic bezier:
    
    ```
    // plot a curve through these coordinates. The target's current coordinates will automatically be added to the start:motionPath: [{x:100, y:50}, {x:200, y:0}, {x:300, y:100}]// cubic bezier coordinates (anchor, two control points, anchor, two control points, etc.):motionPath: {  path: [{x:0, y:0}, {x:20, y:0}, {x:30, y:50}, {x:50, y:50}],  type: "cubic"}
    ```
    
*   An **Array of objects defining _other_ properties** (doesn't need to be "x" and "y"). This will basically smooth out the velocity changes as it hits each value:
    
    ```
    // property values through which to animate (the target's current property values will be added to the start):motionPath: [  { scale: 0.5, rotation: 10 },  { scale: 1, rotation: -10 },  { scale: 0.8, rotation: 3 },];
    ```
    
*   A **configuration object** that has a `path` property with any of the above formats, plus other [configuration details](#usage) like:
    
    ```
    motionPath: {  path: "#pathID",  align: "#pathID",  alignOrigin: [0.5, 0.5],  autoRotate: true,  start: 0.25,  end: 0.75}
    ```
    

## Other features[​](#other-features "Direct link to Other features")

Feature Highlights

*   **Magical `align` capabilities** that bend coordinate systems in order to position the target exactly on top of the path (or move the path to the target), regardless of how deeply nested they are inside different transformed containers! This is insanely convenient and no other tool on the web offers this functionality.
*   `**autoRotate**` makes the target rotate automatically in the direction of the path as it moves.
*   Define specific **`start`** and/or **`end`** positions on the path (progress values from 0-1). Even wrap around or go backwards!
*   A separate [MotionPathHelper](https://gsap.com/docs/v3/Plugins/MotionPathHelper) tool enables **interactive editing of the path directly in the browser!**
*   No need to supply an SVG path - you can provide raw coordinates through which to **plot a curved path, complete with adjustable curviness**
*   Loads of **helper methods** for doing advanced things like:
    *   Convert native SVG shapes like `<circle>`, `<rect>`, etc. into an equivalent `<path>` ([convertToPath()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.convertToPath\(\)))
    *   Calculate the relative position data between any two DOM elements so that you can move one to align perfectly with another, even if they're inside different containers that have various transforms applied! ([getRelativePosition()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getRelativePosition\(\)))
    *   Convert SVG `<path>` data into raw cubic bezier data/numbers (or the other way around) ([stringToRawPath()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.stringToRawPath\(\))/[rawPathToString()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.rawPathToString\(\)))
    *   Convert between coordinate spaces ([convertCoordinates()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.convertCoordinates\(\))/[getGlobalMatrix()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getGlobalMatrix\(\))/[getAlignMatrix()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getAlignMatrix\(\)))

## **Config Object**[​](#config-object "Direct link to config-object")

The `motionPath` can be used as either a shorthand for the `path` (described below) or as a configuration object with any of the following properties: The below code would align a div to an SVG `<path>`. It assumes that there is a DOM element with an `id` of `"div"` and an SVG `<path>` with an `id` of `"#path"`.

*   #### path[](#path)
    
    String | Element | Array \[required\] The motion path along which to animate the target(s). This can be any of the following:
    
    *   An SVG element (selector text or direct reference) like:
        
        // selector text: motionPath: {    path: "#pathID" }  // or direct reference to a  element: let myPath \= document.querySelector("#pathID"); ... motionPath: {    path: myPath }
        
    *   A **string of SVG path data** like:
        
        // path data: motionPath: {    path: "M9,100c0,0,18-41,49-65" }
        
    *   An **Array of objects with x,y coordinates**. A curved path will be plotted **through** these coordinates, or set `type: "cubic"` to have them interpreted as sequential cubic bezier coordinates (ordered like: _anchor, two control points, anchor, two control points_, etc.):
        
        // plot a curve through these coordinates (the target's current coordinates will automatically be added to the start): motionPath: {   path: \[{x:100, y:50}, {x:200, y:0}, {x:300, y:100}\] }  // cubic bezier coordinates (anchor, two control points, anchor, two control points, etc.): motionPath: {   path: \[{x:0, y:0}, {x:20, y:0}, {x:30, y:50}, {x:50, y:50}\],   type: "cubic" }
        
    *   An **Array of objects defining _other_ properties** (doesn't need to be "x" and "y"). This will basically smooth out the velocity changes as it hits each value:
        
        // property values through which to animate (the target's current property values will be added to the start): motionPath: {   path: \[{scale:0.5, rotation:10}, {scale:1, rotation:-10}, {scale:0.8, rotation:3}\] }
        
    
*   #### align[](#align)
    
    String | Element - By default, the raw coordinate values from the `path` data are plugged directly into the target's x/y transforms but the `align` property bends coordinate spaces in order to position the target exactly on top of the path (or move the path to the target) regardless of how deeply nested they are inside different transformed containers! You can align to the `path` too. In other words, `path` and `align` can point to the same element. `align` can be any of the following:
    
    *   **Selector text**, like `"#path"` would select the element with the ID of "path" and move the tween's target so that its top left corner is aligned perfectly with that "#path" element. If you'd rather center the target on the spot, use `alignOrigin: [0.5, 0.5]`
    *   **Element**, like a reference to a DOM element.
    *   **`"self"`** moves the path to the tween's targets so that they don't jump initially. In other words, it's as if the path was drawn from their current position(s).
    
    You can also use `offsetX` and `offsetY` to fine-tune alignment.
    
*   #### alignOrigin[](#alignOrigin)
    
    Array - Determines the point on the target that gets aligned with the path. `alignOrigin` is an Array with progress values along the x and y axis, so `[0.5, 0.5]` would be in the center, `[1, 0]` would be the top right corner, etc. Setting an `alignOrigin` also automatically sets the `transformOrigin` to the corresponding place on the target for convenience. _(added in GSAP 3.2.0)_
    
*   #### autoRotate[](#autoRotate)
    
    Boolean | Number - Rotates the element in the direction of the path. `true` matches the angle of the path exactly, but you can offset the angle by any amount by defining `autoRotate` as a **number** (in degrees). For example, `autoRotate: 90` would add 90 degrees to the rotation as it moves along the path. If you’d like the element to rotate from its center, simply set `transformOrigin: "50% 50%"`. To align the path with the center of the target, either use `alignOrigin: [0.5, 0.5]` or set `xPercent: -50, yPercent: -50` on the target before the motionPath tween.
    
*   #### start[](#start)
    
    Number - The position along the path at which to start, where 0 is the beginning and 1 is the end and 0.5 is the middle. It can be any positive or negative decimal number. For example, `0.3` would start the element at the 30% point along the curve. Default is 0.
    
*   #### end[](#end)
    
    Number - The position along the path at which to end, where 0 is the beginning, 1 is the end, and 0.5 is in the middle. It can be any positive or negative decimal number, including a value that's less than the start (which would make the object travel backwards). For example, `0.3` would have the element end at the 30% point along the curve. 1.5 would make it loop around back to the beginning and stop at the halfway point. Default is 1.
    
*   #### curviness[](#curviness)
    
    Number - Only applies when the `path` is an Array of points through which to plot a curve. This determines how "curvy" the resulting path is. So 0 would make straight lines (hard corners), 1 (the default) creates a nicely curved path, and 2 would make it much more curvy. Think of it like pulling the control points further and further outward from the anchors as the number goes higher. Default is 1.
    
*   #### offsetX[](#offsetX)
    
    Number - An amount to add to the x coordinate(s) for fine-tuning alignment. Default is 0.
    
*   #### offsetY[](#offsetY)
    
    Number - An amount to add to the y coordinate(s) for fine-tuning alignment. Default is 0.
    
*   #### fromCurrent[](#fromCurrent)
    
    Boolean - When `false`, causes it **NOT** to include the current property values in an Array that's passed in for the `path`. For example, if the target is currently at `x: 0`, `y: 0` and then you do a `motionPath: {path: [{x: 100, y: 100}, {x: 200, y: 0}, {x: 300, y: 200}]}` tween, by default it would add `{x: 0, y: 0}` to the _start_ of that Array so that it animates smoothly from wherever it **currently** is but you can set `fromCurrent: false` to avoid that and just have it _jump_ to x: 100, y: 100 at the start of that tween. _(added in 3.7.0)_
    
*   #### relative[](#relative)
    
    Boolean - Only applies when `path` is an Array. If `true`, each successive value is interpreted as **relative** to the previous one. For example, if the target's x starts at 100 and the path is `[{x:5}, {x:10}, {x:-2}]` , it would first move to 105, then 115, and finally end at 113.
    
*   #### type[](#type)
    
    String - Only applies when `path` is an Array of objects with x/y properties - set `type: "cubic"` to have them interpreted as a sequence of cubic beziers in the following order: anchor, two control points, anchor, two control points, anchor, etc. for as many iterations as you want but obviously make sure that it starts and ends with anchors.
    
*   #### resolution[](#resolution)
    
    Number - Only applies when `path` is an Array. Due to the nature of bezier curves, plotting the progression of an object on the path over time can make it appear to speed up or slow down based on the placement of the control points and the length of each successive segment on the path. So MotionPathPlugin implements a technique that reduces or eliminates that variance, but it involves breaking the segments down into a certain number of pieces which is what `resolution` controls. The greater the number, the more accurate the time remapping. But there is a processing price to pay for greater precision. The default value of 12 is typically perfect, but if you notice slight pace changes on the path you can increase the `resolution` value. Or, if you want to prioritize speed you could reduce the number.
    
*   #### useRadians[](#useRadians)
    
    Boolean - If true, the the value passed to the rotation will use radians instead of degrees. This is particularly helpful when working with other scripts or libraries that default to radians like Pixi.js. Default is false.
    

## Demo[​](#demo "Direct link to Demo")

```
gsap.to("#div", {  motionPath: {    path: "#path",    align: "#path",    alignOrigin: [0.5, 0.5],    autoRotate: true,  },  transformOrigin: "50% 50%",  duration: 5,  ease: "power1.inOut",});
```

#### loading...

  CodePen Embed - MotionPathPlugin Demo  

```
<h1>MotionPathPlugin (new in GSAP 3)</h1>

<svg width="100%" height="100%" viewBox="-20 0 557 190" id="svg">
  <circle cx="100" cy="100" r="3" />
  <circle cx="300" cy="20" r="3" />
  <path id="path" d="M9,100c0,0,18.53-41.58,49.91-65.11c30-22.5,65.81-24.88,77.39-24.88c33.87,0,57.55,11.71,77.05,28.47c23.09,19.85,40.33,46.79,61.71,69.77c24.09,25.89,53.44,46.75,102.37,46.75c22.23,0,40.62-2.83,55.84-7.43c27.97-8.45,44.21-22.88,54.78-36.7c14.35-18.75,16.43-36.37,16.43-36.37"/>
  <g id="rect">
    <rect width="85" height="30" fill="dodgerblue" />
    <text x="10" y="19" font-size="14">SVG &lt;rect&gt;</text>
  </g>
</svg>

<div id="div">#div</div>





<link href='//fonts.googleapis.com/css?family=Signika+Negative:300,400' rel='stylesheet' type='text/css'>



<a href="https://greensock.com" target="_blank"><img class="gsap-3-logo" src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/gsap-3-logo.svg" width="150" /></a>
```

```
circle {
  fill: black;
}

html, body {
  height: 100%;
  margin: 0;
  padding: 0;
  overflow: hidden;
}
h1 {
  color: white;
}
#rect text {
  pointer-events: none;
}

body {
  background-color: black;
  color: #999;
  font-family: "Signika Negative", Arial, sans-serif;
  font-weight: 300;
  font-size: 17px;
  min-height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;

}
svg {
  overflow: visible;
  height: 100%;
  
  /* Fix Safari rendering bug */
  transform: translateZ(0);
}

path {
  stroke-width: 2;
  stroke: gray;
}

a {
  color: #88ce02;
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}
#div {
  width: 120px;
  height: 60px;
  pointer-events: none;
  background-color: #aa00ee;
  color: black;
  text-align: center;
  line-height: 60px;
  position: absolute;
  top: 30%;
  left: 60%;
  font-size: 32px;
}





.gsap-3-logo {
    width: 20vw;
    max-width: 150px;
    position: fixed;
    bottom: 15px;
    right: 15px;
}
```

```
//register the plugin (just once)
gsap.registerPlugin(MotionPathPlugin);

gsap.to("#rect", {
  duration: 5, 
  repeat: 12,
  repeatDelay: 3,
  yoyo: true,
  ease: "power1.inOut",
  motionPath:{
    path: "#path",
    align: "#path",
    autoRotate: true,
    alignOrigin: [0.5, 0.5]
  }
});

```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

note

When you `align` the motionPath, those calculations are done at the very start of the animation - it is **NOT** responsive, so if the screen gets resized in a way that affects the path, the alignment won't get re-applied. Why? It would be too expensive CPU-wise to constantly be checking and re-calculating on each tick. But you could definitely set up your own resize listeners and handle it manually in that case (store the progress of the tween, `progress(0).kill()` it, create a new tween and jump to the recorded progress).

## Animating through other properties (not coordinates)[​](#animating-through-other-properties-not-coordinates "Direct link to Animating through other properties (not coordinates)")

You can pass in an Array of objects defining _other_ properties (doesn't need to be "x" and "y") and it will basically smooth out the velocity changes as it hits each value. In the example below, we animate through various `scale` values with a curviness of 0 and 2; notice how the velocity changes are smoother with a higher curviness:

#### loading...

  CodePen Embed - GSAP 3 motionPath applied to scale with curviness  

```
<main>
  <div>
    <div class="box gradient-green" id="box-1"></div>
  <p>curviness: 0</p>
  </div>
  <div>
    <div class="box gradient-green" id="box-2"></div>
     <p>curviness: 2</p>
  </div>
  
  
</main>
```

```
main {
  text-align: center;
  width: 100%; min-height: 100vh;
  display: flex; flex-flow: row nowrap; justify-content: space-evenly; align-items: center;
}

main div {
  display:flex;align-items:center;justify-content:center;flex-direction: column;
}
.box {
  will-change: transform;
  margin-bottom: 2rem;
}
```

```
var scales = [{scale:1.3}, {scale:0.2}, {scale:1}];

gsap.to('#box-1', {
  motionPath: {
    path: scales, 
    curviness: 0
  }, 
  duration: 3, 
  ease: "none",
  repeat: -1,
  repeatDelay: 1
});

gsap.to('#box-2', {
  motionPath: {
    path: scales, 
    curviness: 2
  }, 
  duration: 3, 
  ease: "none",
  repeat: -1,
  repeatDelay: 1
});

```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

## Video[​](#video "Direct link to Video")

## **Methods**[​](#methods "Direct link to methods")

|     |     |
| --- | --- |
| #### [MotionPathPlugin.arrayToRawPath](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.arrayToRawPath\(\))( values:Array, vars:Object ) : RawPath Array | Takes an Array of coordinates and plots a curve through them, returning a corresponding RawPath Array. If `type: "cubic"` is declared in the `vars` parameter object, they will be interpreted as cubic bezier points like anchor, two control points, anchor, two control points, anchor, etc.) |
| #### [MotionPathPlugin.convertCoordinates](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.convertCoordinates\(\))( fromElement:Element \| window, toElement:Element \| window, point:Object ) : Object (point or Matrix2D) | Converts a point from one element's local coordinates into where that point lines up in a different element's local coordinate system regardless of how many nested transforms are affecting the elements! |
| #### [MotionPathPlugin.convertToPath](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.convertToPath\(\))( shape:String \| Element, swap:Boolean ) : Array | Converts SVG shapes like `<circle>`, `<rect>`, `<ellipse>`, or `<line>` into `<path>` |
| #### [MotionPathPlugin.getAlignMatrix](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getAlignMatrix\(\))( fromElement:Element \| window, toElement:Element \| window, fromOrigin:Array, toOrigin:Array \| String ) : Matrix2D | Gets a Matrix2D for translating between coordinate spaces, typically so that you can move the `fromElement` to align it with the `toElement` while factoring in all transforms (even nested ones). The matrix allows you to convert any point/coordinate using its apply() method. |
| #### [MotionPathPlugin.getGlobalMatrix](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getGlobalMatrix\(\))( element:Element, inverse:Boolean, adjustGOffset:Boolean ) : Matrix2D | Gets the Matrix2D that would be used to convert the element's local coordinate space into the global coordinate space. So, for example, if you take a point `{x:0, y:0}` and `apply()` the matrix to it, the resulting point would be the viewport coordinates of that element's top left corner. |
| #### [MotionPathPlugin.getLength](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getLength\(\))( path:Element \| String \| RawPath ) : Number | Returns the length of a path |
| #### [MotionPathPlugin.getPositionOnPath](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getPositionOnPath\(\))( rawPath:Array, progress:Number, includeAngle:Boolean ) : Object | Calculates the x/y position (and optionally the angle) corresponding to a particular progress value along the RawPath |
| #### [MotionPathPlugin.getRawPath](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getRawPath\(\))( value:String \| Element ) : RawPath (Array) | Gets the RawPath (Array) for the provided element or raw SVG <path> data. A RawPath is essentially an Array containing one Array for each contiguous segment with alternating x, y, x, y cubic bezier data. |
| #### [MotionPathPlugin.getRelativePosition](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getRelativePosition\(\))( fromElement:Element \| window, toElement:Element \| window, fromOrigin:Array \| Object, toOrigin:Array \| Object \| String ) : Object | Gets the x and y distances between two elements regardless of nested transforms! feed two elements to this method and it'll return the gap between them as a point {x, y} according to the coordinate system of the fromElement's parent. |
| #### [MotionPathPlugin.pointsToSegment](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/methods/static-pointsToSegment)( points:Array, curviness:Number ) : Array | Plots a curved cubic bezier path through the provided x,y point coordinates, returning a segment Array that's typically dropped into a RawPath Array |
| #### [MotionPathPlugin.rawPathToString](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.rawPathToString\(\))( rawPath:Array ) : String |     |
| #### [MotionPathPlugin.sliceRawPath](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.sliceRawPath\(\))( rawPath:Array, start:Number, end:Number ) : RawPath | Slices the provided RawPath Array at the designated start/end positions and returns the resulting (new, sliced) RawPath |
| #### [MotionPathPlugin.stringToRawPath](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.stringToRawPath\(\))( data:String ) : RawPath |     |

## **Demos**[​](#demos "Direct link to demos")

Check out the full collection of [SVG animation demos](https://codepen.io/collection/NqewVd) on CodePen.

*   [
    
    ### Paper Cut
    
    ](https://codepen.io/aaroniker/pen/RwwZGmj?editors=1000)
*   [
    
    ### Loop
    
    ](https://codepen.io/cassie-codes/pen/mdddaRG?editors=1000)
*   [
    
    ### Object Along MotionPath with Secondary Animation
    
    ](https://codepen.io/mikeK/pen/PoPjXPE)
*   [
    
    ### Object Along MotionPath with Rotation Animation
    
    ](https://codepen.io/GreenSock/pen/GRoXzYj)
*   [
    
    ### Weird Fishes
    
    ](https://codepen.io/michellebarker/pen/dyMQYYz)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
