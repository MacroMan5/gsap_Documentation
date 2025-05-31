# DrawSVG | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/DrawSVGPlugin](https://gsap.com/docs/v3/Plugins/DrawSVGPlugin)  
**Last Updated:** 2025-05-23T00:17:47.855Z  
**Extracted:** 2025-05-31 16:56:03

---

# DrawSVG | GSAP | Docs & Learning

Quick Start

#### CDN Link

```
gsap.registerPlugin(DrawSVGPlugin) 
```

#### Minimal usage

```
//draws all elements with the "draw-me" class applied gsap.from(".draw-me", {duration:1,drawSVG: 0});
```

### Description[​](#description "Direct link to Description")

DrawSVGPlugin allows you to progressively reveal (or hide) the stroke of an SVG `<path>`, `<line>`, `<polyline>`, `<polygon>`, `<rect>`, or `<ellipse>`. You can even animate outward from the center of the stroke (or any position/segment). It does this by controlling the `stroke-dashoffset` and `stroke-dasharray` CSS properties.

Think of the drawSVG value as describing the stroked portion of the overall SVG element (which doesn't necessarily have to start at the beginning). For example, `drawSVG:"20% 80%"` renders the stroke between the 20% and 80% positions, meaning there's a 20% gap on each end. If you started at `"50% 50%"` and animated to `"0% 100%"`, it would draw the stroke from the middle outward to fill the whole path.

#### loading...

  CodePen Embed - DrawSVGPlugin Values  

```

<svg version="1.1"
   xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
   width="516.3px" height="190px" viewBox="0 0 516.3 190" style="enable-background:new 0 0 516.3 211.99;"
   xml:space="preserve">
  <path id="template" d="M9.13,99.99c0,0,18.53-41.58,49.91-65.11c30-22.5,65.81-24.88,77.39-24.88c33.87,0,57.55,11.71,77.05,28.47c23.09,19.85,40.33,46.79,61.71,69.77c24.09,25.89,53.44,46.75,102.37,46.75c22.23,0,40.62-2.83,55.84-7.43c27.97-8.45,44.21-22.88,54.78-36.7c14.35-18.75,16.43-36.37,16.43-36.37"/>
  <path id="path" d="M9.13,99.99c0,0,18.53-41.58,49.91-65.11c30-22.5,65.81-24.88,77.39-24.88c33.87,0,57.55,11.71,77.05,28.47c23.09,19.85,40.33,46.79,61.71,69.77c24.09,25.89,53.44,46.75,102.37,46.75c22.23,0,40.62-2.83,55.84-7.43c27.97-8.45,44.21-22.88,54.78-36.7c14.35-18.75,16.43-36.37,16.43-36.37"/>
</svg>

<div id="code">drawSVG:<div id="current">"100%"</div></div>
<button id="next" class="dark-grey-button club-demo-button" style="display:block; margin-bottom:20px;">Next Example</button>
<!-- https://greensock.com/docs/v3/Plugins/DrawSVGPlugin -->
```

```
body {
  background-color: #1b1b1d;
  color: #ccc;
  text-align: center;
  padding-top: 1rem;
}

#template, #path {
  fill: none;
}
#template {
  stroke-width: 5px;
  stroke: #444;
}
#path {
  stroke: #0ae448;
  stroke-width: 20px;
  visibility: hidden;
}
#code, #value {
  font-size: 2rem;
  font-family: monospace;
}
#code {
  color: #777;
  margin: 20px;
  position: relative;
  visibility:hidden;
}
#current {
  display: inline-block;
  color: white;
}
#description {
  max-width: 530px;
  color: #777;
  font-family: Arial, sans-serif;
  font-size: 1.5rem;
  display: inline-block;
  text-align: left;
}
```

```
var values = "100%;40% 60%;20 350;50% 50%;true;10%".split(";"),
    currentIndex = 0;

//set the initial value
gsap.set("#path, #code", {visibility:"visible"});

function next() {
  
  gsap.killTweensOf(next); //in case the user clicks, clear any delayed calls to this method. 
  if (++currentIndex === values.length) {
    currentIndex = 0;
  }
  if (values[currentIndex] === "true") {
    gsap.set("#current", {text:(values[currentIndex])});
  } else {
    gsap.set("#current", {text:('"' + values[currentIndex] + '"')});
  }
  gsap.to("#path", {drawSVG:values[currentIndex], duration: 1, ease:"power1.inOut"});
  
}

document.querySelector("#next").addEventListener("click", next);
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

Remember, the `drawSVG` value doesn't describe the values between which you want to animate - it describes the end state to which you're animating (or the beginning if you're using a `from()` tween). So `gsap.to("#path", {duration: 1, drawSVG: "20% 80%"})` animates it from wherever the stroke is currently to a state where the stroke exists between the 20% and 80% positions along the path. It does **NOT** animate it from 20% to 80% over the course of the tween.

This is a **good** thing because it gives you much more flexibility. You're not limited to starting out at a single point along the path and animating in one direction only. You control the whole segment (starting and ending positions). So you could even animate a dash from one end of the path to the other, never changing size, like `gsap.fromTo("#path", {drawSVG: "0 5%"}, {duration: 1, drawSVG: "95% 100%"});`

You may use either percentages or absolute lengths. If you use a single value, `0` is assumed for the starting value, so `"100%"` is the same as `"0 100%"` and `"true"`.

**IMPORTANT:** In order to animate the stroke, you must first actually apply one using either CSS or SVG attributes:

```
/* Define a stroke and stroke-width in CSS: */.yourPath {   stroke-width: 10px;  stroke: red;}/* or as SVG attributes: */<path ... stroke-width="10px" stroke="red" />
```

Detailed walkthrough

Introducing DrawSVGPlugin - YouTube

### How do I animate many strokes and stagger animations?[​](#how-do-i-animate-many-strokes-and-stagger-animations "Direct link to How do I animate many strokes and stagger animations?")

The great thing about having DrawSVGPlugin integrated into GSAP is that you can tap into the rich API to quickly create complex effects and have total control (`pause`, `resume`, `reverse`, `seek`, nesting, etc.). So let's say you have 20 SVG elements that all have the class `draw-me` applied to them, and you want to draw them in a staggered fashion. You could do:

```
//draws all elements with the "draw-me" class applied with staggered start times 0.1 seconds apartgsap.from(".draw-me", {duration:1,stagger: 0.1, drawSVG: 0});
```

Or you could create a timeline and drop the tweens into it so that you can control the entire sequence as a whole:

```
var tl = gsap.timeline();tl.from(".draw-me", { duration: 2, drawSVG: 0 }, 0.1); //now we can control it:tl.pause();tl.play();tl.reverse();tl.seek(0.5);...
```

### Add `"live"` to recalculate length throughout animation[​](#add-live-to-recalculate-length-throughout-animation "Direct link to add-live-to-recalculate-length-throughout-animation")

In rare situations, the length of the SVG element itself may change during the drawSVG animation (like if the window is resized and things are responsive). In that case, you can simply append `"live"` to the value which will cause DrawSVGPlugin to update the length on every tick of the animation. So, for example, `drawSVG: "20% 70% live"`.

### Splitting a multi-segment `<path>`[​](#splitting-a-multi-segment-path "Direct link to splitting-a-multi-segment-path")

Usually it's best to use DrawSVGPlugin on `<path>` elements that are just one segment (doesn't contain multiple "M" commands) because browsers have a hard time properly rendering a single stroke through multiple segments, but we've crafted a helper function that automatically splits a multi-segment `<path>` into a `<path>` for each segment, as seen in this demo:

#### loading...

  CodePen Embed - DrawSVG with splitPaths() helper function  

```
<svg width="221" viewBox="30 0 221 167" fill="none" xmlns="http://www.w3.org/2000/svg">
<path id="house" d="M61.0478 144.196V165.498C61.0478 165.498 85.042 166.284 94.0655 165.859C103.091 165.435 125.685 165.259 133.89 165.498C140.208 165.681 146.894 165.683 151.473 165.598C153.401 165.561 154.94 163.996 154.94 162.071V125.831C154.94 124.209 156.257 122.895 157.884 122.895H174.657C176.258 122.895 177.554 124.189 177.554 125.787V162.042C177.554 163.949 178.363 165.101 181.014 165.496C182.785 165.671 219.681 165.659 219.681 165.659M70.6818 102.437H199.213V156.28M66.8866 84.3983V48.0715M193.372 48.367V102.439M121.775 120.183H90.9849C84.9154 120.183 86.7854 140.902 87.0651 143.463C87.3428 146.026 116.088 143.95 120.563 144.531C123.901 144.965 121.775 120.181 121.775 120.181M122.041 63.8285H91.2503C83.5374 63.8285 87.157 84.5369 87.3305 87.1084C88.9086 89.8143 119.73 89.309 120.828 88.1761C123.168 85.7615 122.041 67.2456 122.041 67.2456M173.99 63.8285H143.199C137.13 63.8285 139 84.5471 139.279 87.1084C139.559 89.6717 168.302 87.5953 172.777 88.1761C176.115 88.6101 173.99 67.2456 173.99 67.2456M112.343 18.8418H73.3991L59.5861 48.0715C59.5861 48.0715 93.1101 47.1057 122.706 48.0715C140.982 48.6686 200.674 48.0715 200.674 48.0715L186.861 18.8418H153.25M160.366 143.728C160.914 143.151 161.755 143.053 162.349 143.618C162.945 144.182 162.986 145.107 162.437 145.684C161.889 146.261 160.961 146.269 160.364 145.706C159.768 145.142 159.817 144.305 160.364 143.728H160.366Z" stroke="#0ae448" stroke-width="2.4" stroke-linecap="round" stroke-linejoin="round"/>
</svg>
```

```
body {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background-color: 0e100f;
}

svg {
  overflow: visible;
  width: 100%;
  height: 90vh;
}
```

```
gsap.registerPlugin(MotionPathPlugin, DrawSVGPlugin);

/* 
There's only one <path> but it has a bunch of individual, disconnected segments ("M" commands)
so we'll use the helper function to split that into a bunch of <path> elements so that the browser
can render the stroke progressively in a correct manner.
*/

let paths = splitPaths("#house");
// to animate all the segments at once...
// gsap.from(paths, { drawSVG: 0, duration: 5 });

// but instead, let's animate each segment one-after-the-other and make sure there's a consistent speed.
let duration = 5,
    distance = 0,
    tl = gsap.timeline();
paths.forEach(segment => distance += segment.getTotalLength());
paths.forEach(segment => {
  tl.from(segment, {
    drawSVG: 0,
    ease: "none",
    duration: duration * (segment.getTotalLength() / distance)
  });
});

// helper function that busts apart a single <path> that has multiple segments into a <path> for each segment (indicated by an "M" command);
function splitPaths(paths) {
  let toSplit = gsap.utils.toArray(paths),
      newPaths = [];
  if (toSplit.length > 1) {
    toSplit.forEach(path => newPaths.push(...splitPaths(path)));
  } else {
    let path = toSplit[0],
        rawPath = MotionPathPlugin.getRawPath(path),
        parent = path.parentNode,
        attributes = [].slice.call(path.attributes);
    newPaths = rawPath.map(segment => {
      let newPath = document.createElementNS("http://www.w3.org/2000/svg", "path"),
          i = attributes.length;
      while (i--) {
        newPath.setAttributeNS(null, attributes[i].nodeName, attributes[i].nodeValue);
      }
      newPath.setAttributeNS(null, "d", "M" + segment[0] + "," + segment[1] + "C" + segment.slice(2).join(",") + (segment.closed ? "z" : ""));
      parent.insertBefore(newPath, path);
      return newPath;
    });
    parent.removeChild(path);
  }
  return newPaths;
}
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

### External CSS

1.  [https://codepen.io/GreenSock/pen/JGaKdQ.css](https://codepen.io/GreenSock/pen/JGaKdQ.css)

### External JavaScript

1.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/gsap-latest-beta.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/gsap-latest-beta.min.js)
2.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/CustomEase3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/CustomEase3.min.js)
3.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/DrawSVGPlugin3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/DrawSVGPlugin3.min.js)
4.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/SplitText3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/SplitText3.min.js)
5.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/MorphSVGPlugin3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/MorphSVGPlugin3.min.js)
6.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/Draggable3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/Draggable3.min.js)
7.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/Flip.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/Flip.min.js)
8.  [https://unpkg.com/gsap@3/dist/MotionPathPlugin.min.js](https://unpkg.com/gsap@3/dist/MotionPathPlugin.min.js)
9.  [https://assets.codepen.io/16327/MotionPathHelper.min.js](https://assets.codepen.io/16327/MotionPathHelper.min.js)
10.  [https://assets.codepen.io/16327/GSDevTools3.min.js](https://assets.codepen.io/16327/GSDevTools3.min.js)

### Caveats / Notes[​](#caveats--notes "Direct link to Caveats / Notes")

*   DrawSVGPlugin does not animate the fill of the SVG at all - it only affects the stroke using `stroke-dashoffset` and `stroke-dasharray` CSS properties.
    
*   In some rare situations, Firefox doesn't properly calculate the total length of `<path>` elements, so you may notice that the path stops a bit short even if you animate to 100%. In this (uncommon) scenario, there are two solutions: either add more anchors to your path to make the control points hug closer to the path, or overshoot the percentage a bit, like use `102%` instead of `100%`. To be clear, this is a Firefox bug, not a bug with DrawSVGPlugin.
    
*   As of December 2014, iOS Safari has a bug that causes it to render `<rect>` strokes incorrectly in some cases (too thick, and slight artifacts around the edges, plus it misplaces the origin). The best workaround is to either convert your `<rect>` to a `<path>` or `<polyline>`.
    
*   You cannot affect the contents of a `<use>` element because browsers simply don't allow it. Well, you can tween them but you won't see any changes on the screen.
    

## **Methods**[​](#methods "Direct link to methods")

|     |     |
| --- | --- |
| #### [DrawSVGPlugin.getLength](https://gsap.com/docs/v3/Plugins/DrawSVGPlugin/static.getLength\(\))( element:\[Element \| Selector text\] ) : Number | Provides an easy way to get the length of an SVG element's stroke including: `<path>`, `<rect>`, `<circle>`, `<ellipse>`, `<line>`, `<polyline>`, and `<polygon>` |
| #### [DrawSVGPlugin.getPosition](https://gsap.com/docs/v3/Plugins/DrawSVGPlugin/static.getPosition\(\))( element:\[Element \| Selector text\] ) : Number | Provides an easy way to get the current position of the DrawSVG. |

## **Demos**[​](#demos "Direct link to demos")

Check out the full collection of [How-to demos](https://codepen.io/collection/XRqLgd) and our favourite [inspiring community demos](https://codepen.io/collection/DYmKKD) on CodePen.

*   [
    
    ### Airplanes.
    
    ](https://codepen.io/ste-vg/pen/GRooLza)
*   [
    
    ### Temperature Slider
    
    ](https://codepen.io/chrisgannon/pen/vjNNew)
*   [
    
    ### Space Travel
    
    ](https://codepen.io/shunyadezain/pen/GRNEyZW)
*   [
    
    ### Generative SVG flowers
    
    ](https://codepen.io/natszafraniec/pen/wvzGXMW)
*   [
    
    ### DrawSVG Map Path
    
    ](https://codepen.io/creativeocean/pen/zYrPrgd)
*   [
    
    ### DrawSVG Path on Scroll
    
    ](https://codepen.io/GreenSock/pen/rNOBLBV)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
