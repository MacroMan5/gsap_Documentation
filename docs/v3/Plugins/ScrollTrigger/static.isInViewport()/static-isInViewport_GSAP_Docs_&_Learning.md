# static-isInViewport | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.isInViewport()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.isInViewport())  
**Last Updated:** 2025-05-23T00:33:08.637Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-isInViewport | GSAP | Docs & Learning

## ScrollTrigger.isInViewport

### ScrollTrigger.isInViewport( Element:Element | String, proportion:Number, horizontal:Boolean ) : Boolean

Returns `true` if the element is in the viewport. You can optionally specify a minimum proportion, like `ScrollTrigger.isInViewport(element, 0.2)` would only return `true` if at least 20% of the element is in the viewport.

#### Parameters

*   #### **Element**: Element | String
    
    The element or selector text
    
*   #### **proportion**: Number
    
    The minimum proportion of the element that must be in the viewport to return `true`, so 0.2 would mean that at least 20% of the element must be in the viewport in order for the method to return `true`
    
*   #### **horizontal**: Boolean
    
    By default, the vertical position is evaluated but to use the horizontal position instead, set the horizontal parameter to `true`
    

### Details[​](#details "Direct link to Details")

Returns `true` if the element is in the viewport.

```
// is any part of the element in the viewport?if (ScrollTrigger.isInViewport(element)) {  // you can use selector text  // do stuff}
```

You can optionally specify a minimum proportion, so 0.2 would only return `true` if at least 20% of the element is in the viewport:

```
// at least 20% of the element must be in the viewport for this to return trueif (ScrollTrigger.isInViewport(element, 0.2)) {  // do stuff}
```

By default, it checks the **vertical** position but if you'd like to check the _horizontal_ position instead, set the 3rd parameter to `true` like:

```
// check horizontal instead of verticalif (ScrollTrigger.isInViewport(element, 0.2, true)) {  // do stuff}
```

To find out the precise location of the element within the viewport, see the [ScrollTrigger.positionInViewport()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.positionInViewport\(\)) method.

## Demo[​](#demo "Direct link to Demo")

#### loading...

  CodePen Embed - isInViewport() & positionInViewport() | ScrollTrigger | GSAP  

```
<div class="info">
  <div>
    <div>isInViewport: <span class="viewport">false</span></div>
    <div>positionInViewport: <span class="position">0</span></div>
  </div>
</div>

<div class="scroll-down">Scroll down<br><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" width="20" height="20" class="arrow">
<path fill="white" d="M483.2,192.2c-20.5-20.5-53.5-20.8-73.7-0.6L257,344.1L104.5,191.6c-20.2-20.2-53.2-19.9-73.7,0.6  c-20.5,20.5-20.8,53.5-0.6,73.7l190,190c10.1,10.1,23.4,15.1,36.8,15c13.3,0.1,26.7-4.9,36.8-15l190-190  C503.9,245.7,503.7,212.7,483.2,192.2z"/>
</svg></div>

<div class="box"></div>
```

```
* {
  box-sizing: border-box;
}
body {
  line-height: 1.4;
  font-weight: 300;
  overscroll-behavior: none;
  height: 400vh;
}

.info {
  position: fixed;
  width: 50vw;
  height: 100vh;
  left: 0;
  top: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  align-content: center;
  justify-content: center;
  font-family: monospace;
}
.info div span {
  color: var(--color-orangey);
}

.box {
  position: relative;
  left: 75%;
  top: 150vh;
  transform: translateX(-50%);
}


h1, h2 {
  color: white;
  font-weight: 400;
}
h1 {
  font-size: 40px;
}

.box {
  width: 100px;
  height: 100px;
  position: relative;
  background-color: var(--color-shockingly-green);
  line-height: 100px;
  border-radius: 10px;
}
.scroll-down {
  text-align: center;
  position: relative;
  left: 75%;
  top: 50vh;
  font-size: 1.1em;
  transform: translate(-50%, -50%);
}
```

```
gsap.registerPlugin(ScrollTrigger);

let viewport = document.querySelector(".viewport"),
    position = document.querySelector(".position"),
    box = document.querySelector(".box");

ScrollTrigger.create({
  start: 0,
  end: "max",
  onUpdate: updateValues
});

function updateValues() {
  viewport.innerText = ScrollTrigger.isInViewport(box);
  position.innerText = ScrollTrigger.positionInViewport(box, "center").toFixed(2);
}
updateValues();






// scroll down arrow animation
gsap.to(".arrow", {y: 12, ease: "power1.inOut", repeat: -1, yoyo: true});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
