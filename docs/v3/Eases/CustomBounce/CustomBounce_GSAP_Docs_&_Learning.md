# CustomBounce | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Eases/CustomBounce](https://gsap.com/docs/v3/Eases/CustomBounce)  
**Last Updated:** 2025-05-23T00:14:25.236Z  
**Extracted:** 2025-05-31 16:56:03

---

# CustomBounce | GSAP | Docs & Learning

Quick Start

#### CDN Link

```
gsap.registerPlugin(CustomEase, CustomBounce) 
```

#### Minimal usage

```
//Create a custom bounce ease:CustomBounce.create("myBounce", {  strength: 0.6,  squash: 3,  squashID: "myBounce-squash",});//do the bounce by affecting the "y" property.gsap.from(".class", { duration: 2, y: -200, ease: "myBounce" });//and do the squash/stretch at the same time:gsap.to(".class", {  duration: 2,  scaleX: 1.4,  scaleY: 0.6,  ease: "myBounce-squash",  transformOrigin: "center bottom",});
```

#### loading...

  CodePen Embed - Video: CustomBounce from GreenSock  

```
<svg viewBox="0 0 700 700">
  <line x1="0" x2="700" y1="701" y2="701" stroke="#ccc" stroke-width="2" />
  <path id="bounce" fill="none" stroke="#fffce1" stroke-width="4px" />
  <path id="squash" fill="none" stroke="#abff84" stroke-width="4px" />
  <circle id="ball" fill="#0ae448" r="75" cx="350" cy="75" />
</svg>
<nav id="nav">
  <input id="progressSlider" type="range" min="0" max="1" value="0" step="0.001" />
  <button id="play" class="dark-grey-button club-demo-button">play</button>
</nav>
```

```
body {
  background-color: #0e100f;
  accent-color:#0ae448;
}
svg {
  width:400px;
  position:relative;
  display:block;
  left: 50%;
  z-index: -1;
  overflow: visible;
  transform: translate(-50%, 0%);
}

#progressSlider {
  display:inline-block;
  position:relative;
  width:300px;
}

#nav {
  width:600px;
  margin:10px auto;
  text-align:center;
}

button {
  margin-left:10px;
  padding:10px;
}
```

```
//learn more about CustomBounce and CustomWiggle at: https://greensock.com/wiggle-bounce

var duration = 3;
var tl = gsap.timeline({delay:0.2, onUpdate:updateUI});

//strength between 0 and 1
CustomBounce.create("myBounce", {strength:0.7, squash:3});
tl.to("#ball", {y:550, duration: duration, ease:"myBounce"})
  .to("#ball", {scaleY:0.5, duration: duration, scaleX:1.3, ease:"myBounce-squash", transformOrigin:"bottom"}, 0)




//graph the lines...
//bounce ease green
CustomEase.getSVGData("myBounce", {path:"#bounce", width:700, height:500});
//squash ease red
CustomEase.getSVGData("myBounce-squash", {path:"#squash", width:700, height:500});

progressSlider = document.getElementById("progressSlider");

progressSlider.addEventListener("input", updateAnimation);

function updateAnimation(){
  tl.progress(progressSlider.value).pause();
 
}

function updateUI() {
  progressSlider.value = tl.progress();
}

document.getElementById("play").onclick = function() {
  if(tl.progress() == 1) {
    tl.restart()
  } else {
    tl.play();
  }
}
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

### Description[​](#description "Direct link to Description")

GSAP always has the tried-and-true `"bounce"` ease, but there is no built-in way to customize how "bouncy" it is, nor could you easily get a synchronized squash and stretch effect during the bounce because:

*   The "bounce" ease needs to stick to the ground momentarily at the point of the bounce while the squashing occurs. `"bounce"` offers no such customization.
*   There was no way to create the corresponding \[synchronized\] scaleX/scaleY ease for the squashing/stretching. [CustomEase](https://gsap.com/docs/v3/Eases/CustomEase) solves this now, but it'd still be very difficult to manually draw that ease with all the points lined up in the right spots to match up with the bounces.

With CustomBounce, you can set a few parameters and it'll create **BOTH** CustomEases for you (one for the bounce, and one \[optionally\] for the squash/stretch). Think of CustomBounce like a wrapper that creates a CustomEase under the hood based on the variables you pass in.

CustomBounce extends [CustomEase](https://gsap.com/docs/v3/Eases/CustomEase) (which you must include in your project) and it lets you set the bounce and (optionally) a squash and stretch.

Ease walkthrough

CustomBounce Overview - YouTube

### Options[​](#options "Direct link to Options")

*   #### strength[](#strength)
    
    Number - A number between 0 and 1 that determines how “bouncy” the ease is, so 0.9 will have a lot more bounces than 0.3. Default: `0.7`.
    
*   #### endAtStart[](#endAtStart)
    
    Boolean - If `true`, the ease will end back where it started, allowing you to get an effect like an object sitting on the ground, leaping into the air, and bouncing back down to a stop. Default: `false`.
    
*   #### squash[](#squash)
    
    Number - Controls how long the squash should last (the gap between bounces, when it appears “stuck”). Typically 2 is a good number, but 4 (as an example) would make the squash longer in relation to the rest of the ease. Default: `0`.
    
*   #### squashID[](#squashID)
    
    String - The ID that should be assigned to the squash ease. The default is whatever the ID of the bounce is plus “-squash” appended to the end. For example, `CustomBounce.create("hop", {strength: 0.6, squash: 2})` would default to a squash ease ID of `"hop-squash"`.
    

How do you get the bounce and the squash and stretch to work together? You'd use two tweens; one for the position (`y`), and the other for the `scaleX` and `scaleY`, with both running at the same time:

```
gsap.registerPlugin(CustomEase, CustomBounce); // register//Create a custom bounce ease:CustomBounce.create("myBounce", {  strength: 0.6,  squash: 3,  squashID: "myBounce-squash",});//do the bounce by affecting the "y" property.gsap.from(".class", { duration: 2, y: -200, ease: "myBounce" });//and do the squash/stretch at the same time:gsap.to(".class", {  duration: 2,  scaleX: 1.4,  scaleY: 0.6,  ease: "myBounce-squash",  transformOrigin: "center bottom",});
```

### .getSVGData()[​](#getsvgdata "Direct link to .getSVGData()")

CustomBounce also shares CustomEase's method that calculates the SVG `<path>` data string for visualizing any ease graphically at any size that you define, like `{width: 500, height: 400, x: 10, y: 50}`. You can supply a CustomEase or the ID associated with one, or even a standard ease like `Power2.easeOut`. Feed in a `path` in the vars object and it'll populate its `d` attribute for you, like:

```
//create a CustomEase with an ID of "hop"CustomBounce.create("myBounce", {  strength: 0.6,  squash: 3,  squashID: "myBounce-squash",});//draw the ease visually in the SVG  that has an ID of "ease" at 500px by 400px:CustomEase.getSVGData("myBounce", { width: 500, height: 400, path: "#ease" });
```

### String format[​](#string-format "Direct link to String format")

You can also use GSAP's condensed string formatting for eases, like:

```
ease: "bounce(0.5)"; //<-- easy!ease: "bounce({strength:0.5, endAtStart:true})"; //advanced
```

### **Demos**[​](#demos "Direct link to demos")

[CustomBounce demos](https://codepen.io/collection/DqaLzb)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
