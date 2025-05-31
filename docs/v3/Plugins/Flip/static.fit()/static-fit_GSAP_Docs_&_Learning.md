# static-fit | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Flip/static.fit()](https://gsap.com/docs/v3/Plugins/Flip/static.fit())  
**Last Updated:** 2025-05-23T00:30:07.717Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-fit | GSAP | Docs & Learning

## Flip.fit

### Flip.fit( targetToResize:String | Element, destinationTargetOrState:String | Element | FlipState, vars:Object ) ;

Repositions/resizes one element so that it appears to fit exactly into the same area as another element. Using the `fitChild` special property, you can even scale/reposition an element so that one if its _child_ elements is used for the fitting calculations instead! By default it alters the transforms (x, y, rotation, and skewX) as well as the width and height of the element, but if you set `scale: true` it will use scaleX and scaleY instead of width and height.

#### Parameters

*   #### **targetToResize**: String | Element
    
    The DOM element that should be resized/moved. Can be selector text like `".my-class"` or a reference to the Element itself.
    
*   #### **destinationTargetOrState**: String | Element | FlipState
    
    The DOM element or FlipState that should be fit into.
    
*   #### **vars**: Object
    
    The vars to use for the fit. This can contain standard tweening properties like `ease`, `duration`, `onComplete`, etc. as well as special settings like `absolute`, `fitChild`, `scale`, etc.
    

### Details[​](#details "Direct link to Details")

Repositions/resizes one element so that it appears to fit exactly into the same area as another element. Using the `fitChild` special property, you can even scale/reposition an element so that one if its _child_ elements is used for the fitting calculations instead! By default it alters the transforms (x, y, rotation, and skewX) as well as the width and height of the element, but if you set `scale: true` it will use scaleX and scaleY instead of width and height.

Fitting will occur instantly unless you set a `duration` in the `vars` object in which case it will return a [gsap.to()](https://gsap.com/docs/v3/GSAP/gsap.to\(\)) tween. In fact, you can define almost any standard GSAP tween property there like `onComplete`, `delay`, `ease`, etc. For example:

```
// fit ".box1" into the same area in the viewport as ".box2" immediately:Flip.fit('.box1', '.box2');// or animate there instead:Flip.fit('.box1', '.box2', {    duration: 1,    ease: 'power1.inOut',    onComplete: () => console.log('done!')});
```

You can even use a previously-recorded state object from [Flip.getState()](https://gsap.com/docs/v3/Plugins/Flip/static.getState\(\)) as the destination so that the target fits into the same position/size it was at that time!

```
// capture stateconst state = Flip.getState(box1Element);// change state, like we'll put it into a different container:newParent.appendChild(box1Element);// now fit it into where it was previously:Flip.fit(box1Element, state);
```

How cool is that?

The `vars` object (3rd parameter) can define any of the following \[optional\] configuration properties **in addition to any standard tween properties like `duration`, `ease`, `onComplete`, etc.** which are described [elsewhere](https://gsap.com/docs/v3/GSAP/gsap.to\(\)):

| Property | Description |
| --- | --- |
| absolute | Boolean - if `true`, the target will have its `position` CSS property set to `absolute`. This can solve layout challenges with flex and grid layouts, for example. |
| fitChild | String \| Element - to scale the element so that one of its _child_ elements fits instead, define that child like `fitChild: ".child-class"` (or reference the child Element itself).<br><br>#### loading...<br><br>  CodePen Embed - Flip.fit() fitChild feature  <br><br>```<br><header><br>  <button class="button">Flip.fit() - fit child</button><br></header><br><br><div class="boxes"><br><br>  <div class="target"></div><br><br>  <div class="container"><br>    container<br>    <div class="child1">child1<br>    </div><br>    <div class="child2">child2<br>    </div><br>  </div><br></div><br>```<br><br>```<br>* {<br>  box-sizing: border-box;<br>}<br><br>body {<br>  display: grid;<br>  grid-template-rows: 300px 1fr;<br>  justify-items: stretch;<br>  align-items: center;<br>  overflow: hidden; /* otherwise, if the scrollbar disappears as a result of the tween, the viewport actually gets resized, meaning the measurements are different! */<br>}<br><br>header {<br>  display: flex;<br>  align-items: center;<br>  justify-content: center;<br>  flex-direction: column;<br>}<br><br>.boxes {<br>  display: flex;<br>  align-items: center;<br>  justify-content: space-around;<br>}<br><br>.target {<br>  position: relative;<br>  background: var(--color-ui-gradient);<br>  width: 250px;<br>  height: 120px;<br>  text-align: center;<br>  border-radius: 10px;<br>  color: var(--color-just-black);<br>}<br><br>.container {<br>  width: 40%;<br>  border-radius: 10px;<br>  border: 2px dashed var(--color-surface-white);<br>  text-align: center;<br>  padding: 15px;<br>  pointer-events: none;<br>  display: flex;<br>  flex-direction: column;<br>  align-items: center;<br>  flex-wrap: wrap;<br>}<br>.child1, .child2 {<br>  background: var(--gradient-summer-fair);<br>  height: 120px;<br>  width: 250px;<br>  text-align: center;<br>  margin: 15px 0;<br>  line-height: 100%;<br>  border-radius: 10px;<br>  display: flex;<br>  align-items: center;<br>  justify-content: center;<br>  color: var(--color-just-black);<br>}<br><br>.child1 {<br>  background: transparent;<br>  border: 2px dashed var(--color-surface-white);<br>}<br><br>h1 {<br>  font-weight: 400;<br>}<br><br>.button {<br>  padding: 10px 20px;<br>  margin-bottom: 10px;<br>}<br>.logo {<br>  position: absolute;<br>  width: 60px;<br>  bottom: 20px;<br>  right: 30px;<br>}<br><br>.target:after {<br>  content: "target";<br>  position: absolute;<br>  bottom: 100%;<br>  padding-bottom: 0.5rem;<br>  left: 5px;<br>  color: #888;<br>  font-size: 0.75em;<br>}<br>```<br><br>```<br>gsap.registerPlugin(Flip);<br><br>gsap.to(".container", { rotation: 25});<br>gsap.to(".target", {scale: 1.2, rotation: -18, x: 60, y: 60});<br><br>document.querySelector("button").addEventListener("click", () => {<br>  Flip.fit(".container", ".target", {<br>    fitChild: ".child1",<br>    scale: true, <br>    duration: 2, <br>    ease: "power1.inOut"<br>  });<br>});<br><br>```<br><br>[View Compiled](#0)<br><br>[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)<br><br>This Pen is owned by [GSAP](https://codepen.io/GreenSock) on [CodePen](https://codepen.io/). It is a fork of [this Pen.](https://codepen.io/osublake/fullpage/eJGrPN?default-tab=result&theme-id=41164&view=)<br><br>[See more by @GreenSock on CodePen](https://gsap.com/GreenSock)<br><br>### External CSS<br><br>1.  [https://codepen.io/GreenSock/pen/wvZQKQP.css](https://codepen.io/GreenSock/pen/wvZQKQP.css)<br><br>### External JavaScript<br><br>1.  [https://assets.codepen.io/16327/gsap-latest-beta.min.js](https://assets.codepen.io/16327/gsap-latest-beta.min.js)<br>2.  [https://assets.codepen.io/16327/Flip.min.js](https://assets.codepen.io/16327/Flip.min.js) |
| getVars | Boolean - if `true`, no fitting will occur, but only a vars object will be returned that contains the necessary information for the proper fitting so that it could be passed, for example, to a tween or used separately. For example, if you just want to figure out what the x, y, scaleX, scaleY, rotation, and skewX would be to properly fit, you could do: `let vars = Flip.fit(".box1", ".box2", {scale: true, getVars: true});` |
| props | String - A comma delimited list of CSS properties (beyond the the standard ones that control position, dimensions, rotation, and skew) that should be changed to match the target's. For example, `"backgroundColor,color"` |
| scale | Boolean - by default, Flip.fit() will affect the `width` and `height` CSS properties to alter the size, but if you'd rather scale the element instead (typically better performance), set `scale: true`. The only exception to this behavior is if you define a `fitChild` in which case it will _always_ behave as if `scale: true` was defined (even if you omit it). |
| simple | Boolean - if `true`, Flip will skip the extra calculations that would be necessary to accommodate rotation/scale/skew in determining positions. It's like telling Flip _"I promise that there aren't any rotated/scaled/skewed containers for the Flipping elements"_ which makes things **faster**. In most cases, the performance difference isn't noticeable, but if you're fitting a _lot_ of elements it can help keep things snappy. |

---

*This documentation was extracted from the database for URLs containing 'gsap'*
