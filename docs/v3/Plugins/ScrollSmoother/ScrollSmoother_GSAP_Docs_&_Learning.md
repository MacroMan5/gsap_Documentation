# ScrollSmoother | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollSmoother/](https://gsap.com/docs/v3/Plugins/ScrollSmoother/)  
**Last Updated:** 2025-05-23T00:17:03.642Z  
**Extracted:** 2025-05-31 16:56:03

---

# ScrollSmoother | GSAP | Docs & Learning

added in v3.10.0

Quick Start

#### CDN Link

```
gsap.registerPlugin(ScrollSmoother) 
```

#### Minimal usage

```
ScrollSmoother.create({  smooth: 1,  effects: true,});
```

ScrollSmoother adds a vertical smooth-scrolling effect to a ScrollTrigger-based page. Unlike most smooth-scrolling libraries, ScrollSmoother leverages **NATIVE** scrolling - it doesn't add "fake" scrollbars nor does it mess with touch/pointer functionality. That means it doesn't suffer from many of the accessibility annoyances common with smooth-scrolling sites.

Detailed walkthrough

   Introducing ScrollSmoother for GSAP from GreenSock on Vimeo

Highlights

## Feature Highlights[​](#feature-highlights "Direct link to Feature Highlights")

*   Uses the browser's **native scroll**; no "fake" scrollbars.
*   Add a **parallax effect** by defining a `data-speed` attribute on any element, like `data-speed="0.5"` would make that element "scroll" at half-speed while it's in the viewport. It arrives at its normal position in the document flow when it's **centered** vertically.
*   Put a larger image/element inside a container that has `overflow: hidden` and then set the child's `data-speed="auto"` and it'll automatically calculate exactly how far it can move inside that container (parallax).
*   Make an element appear to **lag behind**, taking a certain amount of time to "catch up" to the smoothed scroll position. It's a really fun effect! Simply define a `data-lag` attribute, like `data-lag="0.5"` would take 0.5 seconds to "catch up".

**read more...**

*   ScrollSmoother is **seamlessly integrated** with [ScrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger) and GSAP for mega-robust animation capabilities.
*   Set [paused(true)](https://gsap.com/docs/v3/Plugins/ScrollSmoother/paused\(\)) to completely halt scrolling (users can't even drag the scrollbar) - great for modals.
*   The `normalizeScroll: true` feature prevents \[most\] mobile browser address bars from hiding/showing (resizing the viewport), stops overscroll behavior, and solves multi-thread synchronization challenges!
*   A side benefit of using ScrollSmoother is that it avoids issues caused by browser multi-threading, like the small jump that sometimes happens when pinning/unpinning, or the occasional "jitter" of a pinned element in certain rare scenarios. You can even set `normalizeScroll: true` to avoid common problems like the hiding/showing of the address bar on mobile browsers, plus it'll work around iOS Safari bugs that occasionally cause jitter. See [ScrollTrigger.normalizeScroll()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.normalizeScroll\(\)) for details.

## Setup[​](#setup "Direct link to Setup")

Your HTML content should reside in a single `content` element (usually a `<div>` but it doesn't really matter) - that's what gets moved around when the user scrolls. That `content` element is wrapped in a `wrapper` element that serves as the viewport. The actual scrollbar remains on the `<body>`, so your setup would look like:

```
<body>  <div id="smooth-wrapper">    <div id="smooth-content">      <!--- ALL YOUR CONTENT HERE --->    </div>  </div>  <!-- position: fixed elements can go outside ---></body>
```

Under the hood, everything flows through [ScrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger) which watches the page's native scroll position and then ScrollSmoother applies transforms to the `content` to gradually catch up with that scroll position. So if you suddenly drag the native scrollbar 500px, ScrollSmoother will gradually move the content to that spot using inline CSS transforms (`matrix3d()`) on the `content`. Since ScrollSmoother is built on top of ScrollTrigger, don't forget to register them both:

```
gsap.registerPlugin(ScrollTrigger, ScrollSmoother);
```

## Example[​](#example "Direct link to Example")

```
// create the scrollSmoother before your scrollTriggersScrollSmoother.create({  smooth: 1, // how long (in seconds) it takes to "catch up" to the native scroll position  effects: true, // looks for data-speed and data-lag attributes on elements  smoothTouch: 0.1, // much shorter smoothing time on touch devices (default is NO smoothing on touch devices)});
```

#### loading...

  CodePen Embed - ScrollSmoother  

```
<div id="smooth-wrapper">
  <div id="smooth-content">
    <header class="header">
      <h1 class="title">ScrollSmoother</h1>
      <button class="button">Jump to C</button>
    </header>
    <div class="box box-a gradient-green" data-speed="clamp(0.5)">a</div>
    <div class="box box-b gradient-purple" data-speed="clamp(0.8)">b</div>
    <div class="box box-c gradient-orange" data-speed="1.5">c</div>
    <div class="line"></div>
  </div>
</div>
```

```
body {
  background-color: var(--color-just-black);
  overscroll-behavior: none;
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

.header {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}


#smooth-content {
  overflow: visible;
  width: 100%;
  /* set a height because the contents are position: absolute, thus natively there's no height */
  height: 4000px;
  background-image:
    linear-gradient(rgba(255,255,255,.07) 2px, transparent 2px),
    linear-gradient(90deg, rgba(255,255,255,.07) 2px, transparent 2px),
    linear-gradient(rgba(255,255,255,.06) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,.06) 1px, transparent 1px);
  background-size: 100px 100px, 100px 100px, 20px 20px, 20px 20px;
  background-position: -2px -2px, -2px -2px, -1px -1px, -1px -1px;
}

button {
  position: relative; 
}

.box {
  width: 100px;
  height: 100px;
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  z-index: 100;
  line-height: 100px;
  text-align: center;
  will-change: transform;
}
.box.active {
  outline: 2px var(--color-surface-white);
}

.box-a {
  top: 200px;
}

.box-b {
  top: 600px;
}

.box-c {
  top: 1000px;
  will-change: transform;
}

.line {
  visibility: hidden;
  width: 2px;
  height: 4000px;
  position: absolute;
  left: 400px;
  top: 0px;
  background-color: #777;
}

.title {
  text-align: center;
  font-weight: 400;
  font-size: 40px;
}
footer {
  position: fixed;
  right: 0px;
  bottom: 0px;
  padding: 6px 10px 10px 12px;
  border-top-left-radius: 26px;
  z-index: 100;
  background-color: rgba(0,0,0,0.5);
}

.end {
  position: absolute;
  /*   bottom: 0; */
  top: 2400px;
  transform: translateY(-100%);
  font-size: 30px;
  color: white;
}
```

```
gsap.registerPlugin(ScrollTrigger, ScrollSmoother);

// create the smooth scroller FIRST!
let smoother = ScrollSmoother.create({
  smooth: 2,
  effects: true,
  normalizeScroll: true
});

// pin box-c when it reaches the center of the viewport, for 300px
ScrollTrigger.create({
  trigger: ".box-c",
  pin: true,
  start: "center center",
  end: "+=300",
  markers: true
});

document.querySelector("button").addEventListener("click", e => {
  // scroll to the spot where .box-c is in the center.
  // parameters: element, smooth, position
  smoother.scrollTo(".box-c", true, "center center");
  
  // or you could animate the scrollTop:
  // gsap.to(smoother, {
  //  scrollTop: smoother.offset(".box-c", "center center"),
  //  duration: 1
  // });
});


// 💚 This just adds the GSAP link to this pen, don't copy this bit
import { GSAPInfoBar } from "https://codepen.io/GreenSock/pen/vYqpyLg.js"
new GSAPInfoBar({ link: "https://gsap.com/docs/v3/Plugins/ScrollSmoother/"});
// 💚 Happy tweening!
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

## **Config Object**[​](#config-object "Direct link to config-object")

The configuration object can have any of the following optional properties:

*   #### content[](#content)
    
    Element | String - the element containing all of your HTML content. This one `content` element is what gets moved around when scrolling. By default, it will automatically find the element with an id of "smooth-content", so if you're following that convention there's no need to even define `content`. The HTML structure would look like this:
    
    ```
    <div id="smooth-wrapper">  <div id="smooth-content">    <!--- ALL YOUR CONTENT HERE --->  </div></div><!-- position: fixed elements can go outside -->
    ```
    
*   #### ease[](#ease)
    
    String | Function - the easing function to be used for smooth scrolling (defaults to "expo").
    
*   #### effects[](#effects)
    
    boolean | String | Array - if `true`, ScrollSmoother will find all elements that have a `data-speed` and/or `data-lag` attribute and apply those effects accordingly so that they move at the designated speed or delay, so `data-speed="0.5"` would scroll at half the normal speed, and `data-speed="2"` would scroll at twice the normal speed. `data-lag="0.8"` would take 0.8 seconds to "catch up" to the smoothed scroll position. You can also use selector text or an Array of elements, so `effects: ".box"` would only look for the attributes on elements with the ".box" class. You can use the [effects()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/effects\(\)) method to apply effects directly via JavaScript instead. See that method's docs for more details about how effects work. _Note: effects should not be nested._
    
*   #### effectsPadding[](#effectsPadding)
    
    Number - Normally effects applied to a particular element begin as soon as the natural position of the element enters the viewport and then end when the natural position leaves the viewport, but in some rare cases you may want to expand that, so you can pass a number (in pixels) as the `effectsPadding`. _Added in 3.11.4_
    
*   #### effectsPrefix[](#effectsPrefix)
    
    String - perhaps you're already using `data-speed` and/or `data-lag` for other purposes and you'd like to use a custom prefix for effects data attributes like `effectsPrefix: "scroll-"` would resolve to `data-scroll-speed` and `data-scroll-lag`. _Added in 3.10.5_
    
*   #### ignoreMobileResize[](#ignoreMobileResize)
    
    Boolean - if `true`, vertical resizes (of 25% of the viewport height) on touch-only devices won't trigger a `ScrollTrigger.refresh()`, avoiding the jumps that can happen when the start/end values are recalculated. Beware that if you skip the refresh(), the start/end trigger positions may be inaccurate but in many scenarios that's preferable to the visual jumps that occur due to the new start/end positions.
    
*   #### onFocusIn[](#onFocusIn)
    
    Function - a function to call when a new element receives focus and you can return `false` if you want ScrollSmoother to skip ensuring that the element is in the viewport (overriding that default behavior).
    
*   #### onStop[](#onStop)
    
    Function - a function to call when the smoothed scroll comes to a stop (catches up to the native scroll position).
    
*   #### onUpdate[](#onUpdate)
    
    Function - a function to call after each time the SmoothScroller updates the position of the content.
    
*   #### normalizeScroll[](#normalizeScroll)
    
    boolean - if `true`, it forces scrolling to be done on the JavaScript thread, ensuring it is synchronized and the address bar doesn't show/hide on mobile devices. This is the same as calling [ScrollTrigger.normalizeScroll()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.normalizeScroll\(\)) except that it _debounces_ because smooth scrolling makes that possible.
    
*   #### smooth[](#smooth)
    
    Number - the time (in seconds) that it takes to "catch up" to the native scroll position. By default, it is 0.8 seconds.
    
*   #### smoothTouch[](#smoothTouch)
    
    Boolean | Number - by default, ScrollSmoother will **NOT** apply scroll smoothing on touch-only devices (like phones) because that typically feels odd to users when it disconnects from their finger's drag position, but you can force smoothing on touch devices too by setting `smoothTouch: true` (same as `smooth` value) or specify an amount like `smoothTouch: 0.1` (in seconds).
    
*   #### speed[](#speed)
    
    Number - a multiplier for overall scroll speed, so `2` would make it scroll twice the normal speed, and `0.5` would make it scroll at half-speed. _added in version 3.11.4_.
    
*   #### wrapper[](#wrapper)
    
    Element | String - the outer-most element that serves as the viewport. Its only child should be the `content` element which is what gets moved around when scrolling. By default, it will automatically find the element with an id of "smooth-wrapper", so if you're following that convention there's no need to even define `wrapper`. If it cannot find a wrapper, one will automatically be created. You can use selector text like `"#elementID"` or reference the element itself.
    

## Speed (parallax)[​](#speed-parallax "Direct link to Speed (parallax)")

When you set `effects: true`, ScrollSmoother finds all elements that have a `data-speed` attribute and applies a parallax effect accordingly so that they move at the designated speed. For example:

```
<div data-speed="0.5"></div><!-- half-speed of scroll --><div data-speed="2"></div><!-- double-speed of scroll --><div data-speed="1"></div><!-- normal speed of scroll --><div data-speed="auto"></div><!-- auto-calculated based on how far it can move inside its container -->
```

### "auto" speed[​](#auto-speed "Direct link to \"auto\" speed")

When you set the speed to `"auto"`, it will calculate how far it can move inside its **parent container** in the direction of the largest gap (up or down). So it's perfect for parallax effects - just make the child larger than its parent, align it where you want it (typically its top edge at the top of the container, or the bottom edge at the bottom of the container) and let ScrollSmoother do its magic. Obviously set `overflow: hidden` on the parent so it clips the child.

### clamp() speed effects[​](#clamp-speed-effects "Direct link to clamp() speed effects")

Have you ever had an element that you natively placed toward the very top of your page but when you apply a `data-speed`, it starts out shifted from its native position? That's because by default, speed effects cause elements to reach their "native" position when **centered vertically** in the viewport, so they'll likely start out offset. Starting in version 3.12, you can wrap your speed value in `"clamp()"` to make them start out in their native position if they're "above the fold" (inside the viewport when scrolled to the very top). Under the hood, `data-speed` effects are driven by ScrollTrigger instances, so this a way to employ ScrollTrigger's clamp() feature that prevents the start/end values from "leaking" outside the page bounds (never less than 0 and never more than the maximum scroll position). For example:

```
<div data-speed="clamp(0.5)"></div><!-- clamped half-speed -->
```

Feature Walkthrough

   Clamp your triggers! from GreenSock on Vimeo

You can also use the [effects()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/effects\(\)) method to dynamically apply speed or lag effects to targets (including function-based ones). _Note: effects **should not be nested**._

```
let scroller = ScrollSmoother.create({...});scroller.effects(".box", {speed: 0.5, lag: 0.1});
```

Keep in mind that the elements will hit their "natural" position in the **CENTER** of the viewport. Here's a visual demo from [@snorkltv](https://www.creativecodingclub.com/courses/FreeGSAP3Express?ref=44f484):

#### loading...

  CodePen Embed - ScrollSmoother Parallax Offsets  

```
<div id="smooth-wrapper">
  <div id="smooth-content">
    <div class="box box-ref">ref</div>
    <div class="box box-a" data-speed="0.5">a</div>
    <div class="box box-b" data-speed="0.5">b</div>
    <div class="box box-c" data-speed="0.5">c</div>
    <div class="refline"></div>
  </div>
</div>
<div class="middle"></div>

<h2>
  ref scrolls normally.<br><br>
  all divs have position of top:80vh.<br><br>
  a, b, and c all have data-speed:0.5<br><br>
  Each object will be at it's "native" placement (with it's top edge aligned to the top of the ref element) when it is centered vertically in the viewport</h2>
```

```
:root {
  --dark: #1d1d1d;
  --grey-dark: #414141;
  --light: #fff;
  --mid: #ededed;
  --grey: #989898;
  --gray: #989898;
  --green: #28a92b;
  --green-dark: #4e9815;
  --green-light: #6fb936;
  --blue: #2c7ad2;
  --purple: #8d3dae;
  --red: #c82736;
  --orange: #e77614;
  accent-color: var(--green);
}
body {
  background-color: #111;
  font-family: "Signika Negative", sans-serif, Arial;
  overscroll-behavior: none;
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}


#smooth-content {
  overflow: visible;
  width: 100%;
  /* set a height because the contents are position: absolute, thus natively there's no height */
  height: 4000px;

  background-image:
    linear-gradient(rgba(255,255,255,.07) 2px, transparent 2px),
    linear-gradient(90deg, rgba(255,255,255,.07) 2px, transparent 2px),
    linear-gradient(rgba(255,255,255,.06) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255,255,255,.06) 1px, transparent 1px);
  background-size: 100px 100px, 100px 100px, 20px 20px, 20px 20px;
  background-position: -2px -2px, -2px -2px, -1px -1px, -1px -1px;
}

button {
  position: relative; 
}

.box {
  width: 100px;
  height: 100px;

background: linear-gradient(#61c3fb 50%, #04a8d8 50%);


  position: absolute;
  z-index: 100;
  line-height: 100px;
  font-size: 30px;
  text-align: center;
  
  will-change: transform;
}
.box-ref {
  top: 80vh;
  left : 100px;

}
.box-a {
  top: 80vh;
  left : 250px;
  height:100px;

}

.box-b {
  left : 400px;
  top: 80vh;
  height:200px
}
.box-c {
  width: 100px;
  height: 400px;
  left : 550px;
  top: 80vh;

}

.middle {
  position:fixed;
  top:50%;
  height:2px;
  width:100%;
  background:red;
  transform:translateY(-50%);
}

.refline {
  position:absolute;
  top:80vh;
  background:purple;
  height:2px;
  width:100%;
  z-index:200;
}

h2 {
  margin:0;
  position:fixed;
  color:#eee;
  padding:1em;
  font-weight:normal;
  background:rgb(0, 0, 0, 0.4);
}
```

```
gsap.registerPlugin(ScrollTrigger, ScrollSmoother);

// create the smooth scroller FIRST!
let smoother = ScrollSmoother.create({
  smooth: 2,   // seconds it takes to "catch up" to native scroll position
  effects: true // look for data-speed and data-lag attributes on elements and animate accordingly
});
```

[![](https://assets.codepen.io/32887/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1559694368&width=256)](https://codepen.io/snorkltv)

## Lag (the delightful kind)[​](#lag-the-delightful-kind "Direct link to Lag (the delightful kind)")

Think of a "lag" like making the element lazy, allowing it to drift from its normal scroll position, taking a certain amount of time to "catch up". You can assign slightly different lags to elements in close proximity to give them a staggered effect when scrolling that's quite pleasing to the eye. If you set `effects: true` on the ScrollSmoother.create() config, it'll automatically find any elements with the `data-lag` attribute and apply that effect:

```
<div data-lag="0.5"></div><!-- takes 0.5 seconds to "catch up" --><div data-lag="0.8"></div><!-- takes 0.8 seconds to "catch up" -->
```

You can also use the [effects()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/effects\(\)) method to dynamically apply speed or lag effects to targets (including function-based ones) via JavaScript.

```
let scroller = ScrollSmoother.create({...});scroller.effects(".box", {lag: 0.5, speed: 1});
```

## Caveats[​](#caveats "Direct link to Caveats")

caution

*   **`position: fixed` should be outside the wrapper** \- since the `content` has a CSS `transform` applied, browsers create a new containing block and that means `position: fixed` elements will be fixed to the `content` rather than the viewport. That's not a bug - it's just how CSS/browsers work. You can use ScrollTrigger pinning instead or you could put any `position: fixed` elements OUTSIDE the `wrapper`/`content`.
*   **`normalizeScroll: true` doesn't prevent the address bar from hiding/showing on iOS phones in portrait orientation** - the latest Apple iOS makes it impossible to prevent that (at least from what we can tell). Even though `event.preventDefault()` is called on all scroll-related events, the browser _still_ imposes that behavior. If that causes a jump due to the window resizing and making your ScrollTriggers recalculate their start/end positions, you could `ScrollTrigger.config({ ignoreMobileResize: true });`

## **Properties**[​](#properties "Direct link to properties")

|     |     |
| --- | --- |
| #### [.progress](https://gsap.com/docs/v3/Plugins/ScrollSmoother/progress) : Number | The progress value of the overall page scroll where 0 is at the very top and 1 is at the very bottom and 0.5 is halfway scrolled. This value will animate during the smooth scrolling and end when the `onStop` fires. |
| #### [.scrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollSmoother/scrollTrigger) : ScrollTrigger | The ScrollTrigger instance that ScrollSmoother created internally to manage the smooth scrolling effect of the page. |
| #### [.vars](https://gsap.com/docs/v3/Plugins/ScrollSmoother/vars) : Object |     |

## **Methods**[​](#methods "Direct link to methods")

|     |     |
| --- | --- |
| #### [.content](https://gsap.com/docs/v3/Plugins/ScrollSmoother/content\(\))( element:String \| Element ) : Element \| self | Gets/Sets the content element. |
| #### [.effects](https://gsap.com/docs/v3/Plugins/ScrollSmoother/effects\(\))( targets:String \| Element \| Array, config:Object \| null ) : Array | Adds parallax elements that should be managed by the ScrollSmoother |
| #### [.getVelocity](https://gsap.com/docs/v3/Plugins/ScrollSmoother/getVelocity\(\))( ) : Number | Returns the current velocity of the smoothed scroll in pixels-per-second |
| #### [.kill](https://gsap.com/docs/v3/Plugins/ScrollSmoother/kill\(\))( ) ; | Kills the entire ScrollSmoother as well as any effects that were applied. |
| #### [.offset](https://gsap.com/docs/v3/Plugins/ScrollSmoother/offset\(\))( target:String \| Element, position:String ) : Number | Calculates the numeric offset (scroll position in pixels) that corresponds to when a particular element reaches the specified position like: |
| #### [.paused](https://gsap.com/docs/v3/Plugins/ScrollSmoother/paused\(\))( pause:Boolean ) : Boolean \| self | Gets/Sets the paused state - if `true`, nothing will scroll (except via [scrollTop()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/scrollTop\(\)) or [scrollTo()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/scrollTo\(\)) on this instance). |
| #### [.scrollTo](https://gsap.com/docs/v3/Plugins/ScrollSmoother/scrollTo\(\))( target:Number \| String \| Element, smooth:Boolean, position:String ) ; | Scrolls to a particular position or element |
| #### [.scrollTop](https://gsap.com/docs/v3/Plugins/ScrollSmoother/scrollTop\(\))( position:Number ) : Number \| void | Immediately gets/sets the scroll position (in pixels). |
| #### [.smooth](https://gsap.com/docs/v3/Plugins/ScrollSmoother/smooth\(\))( duration:Number ) : Number \| self | Gets/Sets the number of seconds it takes to catch up to the scroll position (smoothing). |
| #### [ScrollSmoother.create](https://gsap.com/docs/v3/Plugins/ScrollSmoother/static.create\(\))( ) ; |     |
| #### [ScrollSmoother.get](https://gsap.com/docs/v3/Plugins/ScrollSmoother/static.get\(\))( ) : ScrollSmoother | Returns the ScrollSmoother instance (if one has been created). There can only be one instance at any given time. |
| #### [.wrapper](https://gsap.com/docs/v3/Plugins/ScrollSmoother/wrapper\(\))( element:String \| Element ) : Element \| self | Gets/Sets the wrapper element. |

## **Demos**[​](#demos "Direct link to demos")

Check out the full collection of [Scroll animation demos](https://codepen.io/collection/bNPYOw) on CodePen.

*   [
    
    ### Scrolly Images
    
    ](https://codepen.io/GreenSock/pen/xxXadQJ)
*   [
    
    ### Split Header
    
    ](https://codepen.io/GreenSock/pen/NWXjBOa)
*   [
    
    ### Drag Demo
    
    ](https://codepen.io/vanholtzco/pen/abEOead)
*   [
    
    ### Rainbow Scroll
    
    ](https://codepen.io/supah/pen/MWroVZG)
*   [
    
    ### Clamp
    
    ](https://codepen.io/GreenSock/pen/JjmLLWZ)
*   [
    
    ### Data Speed
    
    ](https://codepen.io/GreenSock/pen/jOjMQjr)
*   [
    
    ### GSAP ScrollSmoother + Three.js
    
    ](https://codepen.io/cmalven/pen/PoEJvjE)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
