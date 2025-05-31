# effects | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollSmoother/effects()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/effects())  
**Last Updated:** 2025-05-23T00:27:48.838Z  
**Extracted:** 2025-05-31 16:56:03

---

# effects | GSAP | Docs & Learning

### .effects( targets:String | Element | Array, config:Object | null ) : Array

Adds parallax elements that should be managed by the ScrollSmoother

#### Parameters

*   #### **targets**: String | Element | Array
    
    The target elements that should have the effects applied. You can use selector text like `".box"` or use an element reference or an Array of elements.
    
*   #### **config**: Object | null
    
    A config object that can contain `speed` and/or `lag` properties like `{speed: 1, lag: 0.3}`. If omitted, ScrollSmoother will just use each element's `data-speed` or `data-lag` attribute value. Function-based values are accepted as well just like most places in GSAP.
    

### Returns : Array[​](#returns--array "Direct link to Returns : Array")

An Array of ScrollTrigger instances that were created to handle the effects

### Details[​](#details "Direct link to Details")

Adds **speed** or **lag** effects to the supplied targets. Use "speed" to get parallax effects. Think of a "lag" like making the element lazy, allowing it to drift from its normal scroll position, taking a certain amount of time to "catch up". You can assign slightly different lags to elements in close proximity to give them a staggered effect when scrolling that's quite pleasing to the eye. If you set `effects: true` on the [ScrollSmoother.create()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/static.create\(\)) config, it'll automatically find any elements with the `data-lag` attribute and apply that effect, or you can use this function to apply them via JavaScript:

```
let smoother = ScrollSmoother.create(...);// use the data-speed and data-lag attributes found on each .box elementsmoother.effects(".box");// or specify values:smoother.effects(".circle", {speed: 0.9, lag: 0.3});
```

You can remove effects by setting them to the defaults like:

```
// remove effects by setting back to defaultssmoother.effects(".box", { speed: 1, lag: 0 });
```

When an effect is applied to an element, ScrollSmoother just creates a [ScrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger) instance to manage the effect, and it returns an Array of those ScrollTrigger instances. So if you apply a "speed" effect to 5 elements, the returned Array will contain 5 ScrollTrigger instances. You can also get an Array of ALL effects by using the method as a getter:

```
// returns an Array of all the ScrollTrigger instances that are managing the effectslet effects = smoother.effects(); // getter// kill all the effects:smoother.effects().forEach((t) => t.kill());
```

## "auto" speed[​](#auto-speed "Direct link to \"auto\" speed")

When you set the speed to `"auto"`, it will calculate how far it can move inside its **parent container** in the direction of the largest gap (up or down). So it's perfect for parallax effects - just make the child larger than its parent, align it where you want it (typically its top edge at the top of the container, or the bottom edge at the bottom of the container) and let ScrollSmoother do its magic. Obviously set `overflow: hidden` on the parent so it clips the child.

You can even use **function-based values** to make things even more dynamic:

```
smoother.effects(".box", {  speed: (index, element) => 0.5 + index * 0.1,  lag: (index, element) => 0.3 + index * 0.05,});
```

These function-based values will get refreshed whenever [ScrollTrigger.refresh()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.refresh\(\)) is called.

### data-speed alignment[​](#data-speed-alignment "Direct link to data-speed alignment")

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

---

*This documentation was extracted from the database for URLs containing 'gsap'*
