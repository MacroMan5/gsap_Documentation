# static-create | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollSmoother/static.create()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/static.create())  
**Last Updated:** 2025-05-23T00:28:06.412Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-create | GSAP | Docs & Learning

## ScrollSmoother.create

### ScrollSmoother.create( ) ;

### Details[​](#details "Direct link to Details")

Creates (and returns) a new ScrollSmoother instance. There can only be one, of course, at any given time because it's controlling the scroll of the root page. If a ScrollSmoother instance already exists, its [kill()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/kill\(\)) method will be called before creating the new one in the `ScrollSmoother.create()` call. If you want to get a reference to the ScrollSmoother that was already created, use the [ScrollSmoother.get()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/static.get\(\)) method.

## Setup[​](#setup "Direct link to Setup")

Your HTML content should reside in a single `content` element (usually a`<div>`but it doesn't really matter) - that's what gets moved around when the user scrolls. That `content` element is wrapped in a `wrapper` element that serves as the viewport. The actual scrollbar remains on the `<body>`, so your setup would look like:

```
<body>  <div id="smooth-wrapper">    <div id="smooth-content">      <!--- ALL YOUR CONTENT HERE --->    </div>  </div></body>
```

Under the hood, everything flows through [ScrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger) which watches the page's native scroll position and then ScrollSmoother applies transforms to the `content` to gradually catch up with that scroll position. So if you suddenly drag the native scrollbar 500px, ScrollSmoother will gradually move the content to that spot using inline CSS transforms (`matrix3d()`) on the `content`. Since ScrollSmoother is built on top of ScrollTrigger, don't forget to register them both:

```
gsap.registerPlugin(ScrollTrigger, ScrollSmoother);
```

## Usage & special properties[​](#usage--special-properties "Direct link to Usage & special properties")

The configuration object can have any of the following optional properties:

## Speed (parallax)[​](#speed-parallax "Direct link to Speed (parallax)")

When you set `effects: true`, ScrollSmoother finds all elements that have a `data-speed` attribute and applies a parallax effect accordingly so that they move at the designated speed. For example:

```
<div data-speed="0.5"></div> <!-- half-speed of scroll --><div data-speed="2"></div> <!-- double-speed of scroll --><div data-speed="1"></div> <!-- normal speed of scroll --><div data-speed="auto"></div> <!-- auto-calculated based on how far it can move inside its container -->
```

### "auto" speed[​](#auto-speed "Direct link to \"auto\" speed")

When you set the speed to `"auto"`, it will calculate how far it can move inside its **parent container** in the direction of the largest gap (up or down). So it's perfect for parallax effects - just make the child larger than its parent, align it where you want it (typically its top edge at the top of the container, or the bottom edge at the bottom of the container) and let ScrollSmoother do its magic. Obviously set `overflow: hidden` on the parent so it clips the child.

### clamp() speed effects[​](#clamp-speed-effects "Direct link to clamp() speed effects")

Have you ever had an element that you natively placed toward the very top of your page but when you apply a `data-speed`, it starts out shifted from its native position? That's because by default, speed effects cause elements to reach their "native" position when **centered vertically** in the viewport, so they'll likely start out offset. Starting in version 3.12, you can wrap your speed value in `"clamp()"` to make them start out in their native position if they're "above the fold" (inside the viewport when scrolled to the very top). Under the hood, `data-speed` effects are driven by ScrollTrigger instances, so this a way to employ ScrollTrigger's clamp() feature that prevents the start/end values from "leaking" outside the page bounds (never less than 0 and never more than the maximum scroll position). For example:

```
<div data-speed="clamp(0.5)"></div> <!-- clamped half-speed -->
```

Walkthrough

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
<div data-lag="0.5"></div> <!-- takes 0.5 seconds to "catch up" --><div data-lag="0.8"></div> <!-- takes 0.8 seconds to "catch up" -->
```

You can also use the [effects()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/effects\(\)) method to dynamically apply speed or lag effects to targets (including function-based ones) via JavaScript.

```
let scroller = ScrollSmoother.create({...});scroller.effects(".box", {lag: 0.5, speed: 1});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
