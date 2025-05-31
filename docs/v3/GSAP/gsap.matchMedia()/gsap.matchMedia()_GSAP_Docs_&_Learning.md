# gsap.matchMedia() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.matchMedia()](https://gsap.com/docs/v3/GSAP/gsap.matchMedia())  
**Last Updated:** 2025-05-23T00:15:21.547Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.matchMedia() | GSAP | Docs & Learning

added in v3.11.0

Quick Start

#### Minimal usage

```
// createlet mm = gsap.matchMedia();// add a media query. When it matches, the associated function will runmm.add("(min-width: 800px)", () => {  // this setup code only runs when viewport is at least 800px wide  gsap.to(...);  gsap.from(...);  ScrollTrigger.create({...});  return () => { // optional    // custom cleanup code here (runs when it STOPS matching)  };});// later, if we need to revert all the animations/ScrollTriggers...mm.revert();
```

### Returns : MatchMedia[​](#returns--matchmedia "Direct link to Returns : MatchMedia")

Detailed walkthrough

Responsive & Accessible Animation with gsap.matchMedia() - YouTube

Responsive, accessible animations and ScrollTriggers, here you come! 🥳 `gsap.matchMedia()` lets you tuck setup code into a function that only executes when a particular [media query](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) matches and then when it no longer matches, all the GSAP animations and [ScrollTriggers](https://gsap.com/docs/v3/Plugins/ScrollTrigger) created during that function's execution get **reverted automatically**! Customizing for mobile/desktop or `prefers-reduced-motion` accessibility is remarkably simple.

Each [media query string](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) is exactly what you'd pass into the browser's native [window.matchMedia()](https://developer.mozilla.org/en-US/docs/Web/API/MediaQueryList#Examples)

## Basic syntax[​](#basic-syntax "Direct link to Basic syntax")

```
// createlet mm = gsap.matchMedia();// add a media query. When it matches, the associated function will runmm.add("(min-width: 800px)", () => {  // this setup code only runs when viewport is at least 800px wide  gsap.to(...);  gsap.from(...);  ScrollTrigger.create({...});  return () => { // optional    // custom cleanup code here (runs when it STOPS matching)  };});// later, if we need to revert all the animations/ScrollTriggers...mm.revert();
```

We create a `mm` variable for the MatchMedia so that we can `add()` as many media queries as we want to that one object. That way, we have a single object on which we can call `revert()` to instantly revert all the animations/ScrollTriggers that were created in any of the associated MatchMedia functions.

The function gets invoked whenever it becomes active (matches). So if a user resizes the browser past the breakpoint and back again multiple times, the function would get called multiple times.

### .add() parameters[​](#add-parameters "Direct link to .add() parameters")

1.  **query/conditions** - a [media query string](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) like `"(min-width: 800px)"`**\-OR-** a [conditions object](#conditions) with as many arbitrarily-named query strings as you'd like; you'll be able to check the matching status of each (boolean). See [below](#conditions) for details about the conditions syntax.
2.  **handler function** - the function to invoke when there's a match. All GSAP animations and ScrollTriggers created during execution of this function will be collected in the context so that they can be reverted when the MatchMedia gets reverted (like when the condition stops matching).
3.  **scope** _\[optional\]_ - all GSAP-related selector text inside the handler function will be scoped to this Element or [React Ref](https://reactjs.org/docs/refs-and-the-dom.html) or [Angular ElementRef](https://angular.io/api/core/ElementRef). Think of it like calling `querySelectorAll()` on this element, so only its descendants can be selected. See [below](#scope) for details.

So the structure looks like:

```
mm.add("(min-width: 800px)", () => {...}, myElementOrRef);
```

### Simplistic desktop/mobile example[​](#simplistic-desktopmobile-example "Direct link to Simplistic desktop/mobile example")

```
let mm = gsap.matchMedia();mm.add("(min-width: 800px)", () => {  // desktop setup code here...});mm.add("(max-width: 799px)", () => {  // mobile setup code here...});
```

## Conditions syntax[​](#conditions-syntax "Direct link to Conditions syntax")

What if your setup code for various media queries is mostly identical but a few key values are different? If you `add()` each media query individually, you may end up with a lot of **redundant code**. Just use the conditions syntax! Instead of a string for the first parameter, use an **object with arbitrarily-named conditions** and then the function will get called when **any** of those conditions match and you can check each condition as a boolean (matching or not). The conditions object could look like this:

```
{  isDesktop: "(min-width: 800px)",  isMobile: "(max-width: 799px)",  reduceMotion: "(prefers-reduced-motion: reduce)"}
```

Name your conditions whatever you want.

Below we'll set the breakpoint at 800px wide and honor the user's `prefers-reduced-motion` preference, leveraging the same setup code and using conditional logic where necessary:

```
let mm = gsap.matchMedia(),  breakPoint = 800;mm.add(  {    // set up any number of arbitrarily-named conditions. The function below will be called when ANY of them match.    isDesktop: `(min-width: ${breakPoint}px)`,    isMobile: `(max-width: ${breakPoint - 1}px)`,    reduceMotion: "(prefers-reduced-motion: reduce)",  },  (context) => {    // context.conditions has a boolean property for each condition defined above indicating if it's matched or not.    let { isDesktop, isMobile, reduceMotion } = context.conditions;    gsap.to(".box", {      rotation: isDesktop ? 360 : 180, // spin further if desktop      duration: reduceMotion ? 0 : 2, // skip to the end if prefers-reduced-motion    });    return () => {      // optionally return a cleanup function that will be called when none of the conditions match anymore (after having matched)      // it'll automatically call context.revert() - do NOT do that here . Only put custom cleanup code here.    };  });
```

Nice and concise! 🎉

It will revert and run the handler function again if/when **any** of the conditions toggle (it won't run again if none of them match, of course). For example, if you have three conditions and two of them match, it will run. Then if one of the matching queries _STOPS_ matching (toggles to `false`), it'll revert and run the function again with updated condition values.

Notice that [Context](https://gsap.com/docs/v3/GSAP/gsap.context\(\)) is created and passed in as the only parameter. This can be useful if you need to create event handlers or execute other code later that creates animations/ScrollTriggers which should be reverted when `revert()` is called on the MatchMedia.

## Demo using conditional syntax[​](#demo-using-conditional-syntax "Direct link to Demo using conditional syntax")

#### loading...

  CodePen Embed - gsap.matchMedia() Demo  

```
<header>
  <h1>gsap.matchMedia()</h1>
  <p class="lead">When the viewport is less than 800px, the "Mobile" &lt;div&gt; will animate. Otherwise, "Desktop" will.</p>
</header>
<section class="gray">
  <div class="mobile">Mobile</div>
  <div class="desktop">Desktop</div>
</section>

<section class="bottom lead">
  <p><strong>Pretty cool, right?</strong></p>
  <p>Resize your screen. 800px is the break point. It's all dynamic!</p>
  <p>Check out <a href="https://greensock.com">GSAP</a> today. </p>
</section>
```

```
/* external styles https://codepen.io/GreenSock/pen/xxmzBrw/fcaef74061bb7a76e5263dfc076c363e.css */

body {
  text-align: center;
  font-weight: 300;
}

header {
  padding: 0 1rem;
  margin: 0 auto;
}

h1 {
  margin: 0;
  padding: 35px 10px;
  font-weight: 400;
}

.gray {
  position: relative;
  width: 100%;
  height: 100vh;
}

.mobile, .desktop {
  width: 200px;
  height: 100px;
  border-radius: 5px;
  background: var(--purple);
  position: absolute;
  z-index: 0;
  left: 30%;
  top: 50%;
  transform: translate3d(-50%, -50%, 0);
  text-align: center;
  font-size: 1.5em;
  font-weight: 400;
  line-height: 100px;
  color: white;
}

.desktop {
  left: 70%;
  background: var(--green);
}

.gray p {
  margin: 0;
  padding: 30px;
}

.bottom {
  width: 100%;
  text-align: center;
  padding: 150px 30px;
  font-size: 1.5em;
  box-sizing: border-box;
}


a {
  text-decoration: none;
  font-weight: 400;
}

a:hover {
  text-decoration: underline;
}

@media (max-width: 799px) { 
  .mobile, .desktop {
    width: 100px;
  }
}
```

```
gsap.registerPlugin(ScrollTrigger);

let mm = gsap.matchMedia(),
    breakPoint = 800;

mm.add({
  // set up any number of arbitrarily-named conditions. The function below will be called when ANY of them match.
  isDesktop: `(min-width: ${breakPoint}px) and (prefers-reduced-motion: no-preference)`,
  isMobile: `(max-width: ${breakPoint - 1}px) and (prefers-reduced-motion: no-preference)`
}, (context) => {
  // context.conditions has a boolean property for each condition defined above indicating if it's matched or not.
  let { isDesktop, isMobile } = context.conditions,
      target = isDesktop ? ".desktop" : ".mobile",
      tl = gsap.timeline({
        scrollTrigger: {
          trigger: ".gray",
          scrub: 1,
          end: "200%",
          pin: true
        }
      });
  tl.to(target, {scale: 2, rotation: 360})
    .to(target, {scale: 1});

  // works for non-ScrollTrigger animations too: 
  gsap.to(target, {backgroundColor: "#2c7ad2", duration: 0.8, ease: "none", repeat: -1, yoyo: true});

  return () => { 
    // optionally return a cleanup function that will be called when the media query no longer matches
  }
}); 
  
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

## Interactivity and cleanup[​](#interactivity-and-cleanup "Direct link to Interactivity and cleanup")

The GSAP animations and ScrollTriggers created while the function is executed get recorded in the [Context](https://gsap.com/docs/v3/GSAP/gsap.context\(\)), but what if you set up event listeners, like for "click" events which run sometime later, **after** the MatchMedia function is done executing? You can add() a named function to the Context object itself so that when it runs, any animations/ScrollTriggers created in that function get collected in the Context, like:

```
let mm = gsap.matchMedia();mm.add("(min-width: 800px)", (context) => {  context.add("onClick", () => {    gsap.to(".box", { rotation: 360 }); // <- now it gets recorded in the Context  });  myButton.addEventListener("click", context.onClick);  return () => {    // make sure to clean up event listeners in the cleanup function!    myButton.removeEventListener("click", context.onClick);  };});
```

## Scoping selector text[​](#scoping-selector-text "Direct link to Scoping selector text")

You can optionally pass in an Element or [React Ref](https://reactjs.org/docs/refs-and-the-dom.html) or [Angular ElementRef](https://angular.io/api/core/ElementRef) as the 3rd parameter and then **all** the selector text in the supplied function will be scoped to that particular Element/Ref (like calling `querySelectorAll()` on that Element/Ref).

```
let mm = gsap.matchMedia();mm.add("(min-width: 800px)", () => {  gsap.to(".box", {...}) // <- normal selector text, automatically scoped to myRefOrElement}, myRefOrElement); // <- scope!!!
```

The `scope` can be selector text itself like `".myClass"`, or an Element, React Ref or Angular ElementRef.

Set a **default scope** when you create the MatchMedia by passing it in as the only parameter:

```
let mm = gsap.matchMedia(myRefOrElement);mm.add("(min-width: 800px)", () => {  // selector text scoped to myRefOrElement  gsap.to(".class", {...});});mm.add("(max-width: 799px)", () => {  // selector text scoped to myOtherElement  gsap.to(".class", {...});}, myOtherElement); // <- overrides default scope!!!
```

## Refreshing all matches[​](#refreshing-all-matches "Direct link to Refreshing all matches")

Use [gsap.matchMediaRefresh()](https://gsap.com/docs/v3/GSAP/gsap.matchMediaRefresh\(\)) to immediately revert all active/matching MatchMedia objects and then run any that currently match. This can be very useful if you need to accommodate a UI checkbox that toggles a reduced motion preference, for example.

## Accessible animations with prefers-reduced-motion[​](#accessible-animations-with-prefers-reduced-motion "Direct link to Accessible animations with prefers-reduced-motion")

We all love animation here, but it can make some users with vestibular disorders feel nauseous. It's important to respect their preferences and either serve up minimal animation, or no animation at all. We can tap into the prefers reduced motion media query for this

### simple demo[​](#simple-demo "Direct link to simple demo")

#### loading...

  CodePen Embed - gsap.matchMedia() Demo - reduced motion  

```
<header class="center pad-l">
  <h1>gsap.matchMedia()</h1>
  <p class="lead">Use matchMedia for easy, accessibility friendly animation.</p>
</header>


<section class="panel">
  <div class="box green"></div>
</section>

<section class="bottom">
  <p><strong>Pretty cool, right?</strong></p>
  <p>You can read more about reduced motion and vestibular disorders in this <a href="https://css-tricks.com/introduction-reduced-motion-media-query/">blog post</a> on CSS tricks</p>
  <p>How do I <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion#user_preferences">adjust my reduced motion setting?</a></p>
  <p>Check out <a href="https://greensock.com">GSAP</a> today. </p>
</section>
```

```
header {
  flex-direction: column;
}
.panel {
  display: flex;
  align-items: center;
  justify-content: center;
}

.gray p {
  color: #ccc;
  font-size: 1.4em;
  margin: 0;
  padding: 30px;
  line-height: 1.4em;
}

.bottom {
  width: 100%;
  text-align: center;
  padding: 150px 30px;
  font-size: 1.2em;
  box-sizing: border-box;
}
```

```
gsap.registerPlugin(ScrollTrigger);

let mm = gsap.matchMedia()

mm.add("(prefers-reduced-motion: no-preference)", (context) => {
    let tl = gsap.timeline({
      scrollTrigger: {
        trigger: ".gray",
        scrub: 1,
        end: "max",
        pin: true
      }
    });
    tl.to(".box", { scale: 2}).to(".box", { scale: 1 });

    gsap.to(".box", {
      rotation: 360,
      ease: "none",
      duration: 4,
      repeat: -1,
    });
  }
);

// a 'reduced' motion animation
mm.add("(prefers-reduced-motion: reduce)", (context) => {
    let tl = gsap.timeline({
      scrollTrigger: {
        trigger: ".gray",
        scrub: 1,
        end: "max",
        pin: true,
        markers: true,
      }
    });
    tl.to(".box", { scale: 1.5}).to(".box", { scale: 1 });
  }
);
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

### checkbox toggle[​](#checkbox-toggle "Direct link to checkbox toggle")

#### loading...

  CodePen Embed - gsap.matchMedia() Demo - reduced motion toggle  

```
<header class="center pad-l">
  <h1>gsap.matchMedia()</h1>
  <p class="lead">Use matchMedia and the prefers-reduced-motion media feature for easy, accessibility-friendly animation.</p>
  <div class="checkbox">
  <input type="checkbox" id="motionToggle" class="vh" name="motionToggle" value="false">
  <label for="motionToggle">Reduced animation please</label>
</div>
</header>


<section class="gray">
  <div class="box gradient-green"></div>
</section>

<section class="bottom">
  <p><strong>Pretty cool, right?</strong></p>
  <p>You can read more about reduced motion and vestibular disorders in this <a href="https://css-tricks.com/introduction-reduced-motion-media-query/">blog post</a> on CSS tricks</p>
  <p>How do I <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion#user_preferences">adjust my reduced motion setting?</a></p>
  <p>Check out <a href="https://greensock.com">GSAP</a> today. </p>
</section>
```

```
header {
  flex-direction: column;
}

.lead {
  padding: 0 20px;
  text-align: center;
}

.gray {
  width: 100%;
  height: 100vh;
}
.box {
  width: 150px;
  height: 150px;
  position: absolute;
  z-index: 0;
  left: 50%;
  top: 50%;
  transform: translate3d(-50%, -50%, 0);
}

.gray p {
  font-size: 1.4em;
  margin: 0;
  padding: 30px;
  line-height: 1.4em;
}

.bottom {
  width: 100%;
  text-align: center;
  padding: 150px 30px;
  font-size: 1.2em;
  box-sizing: border-box;
}
```

```
gsap.registerPlugin(ScrollTrigger);

let reduceMotionCB = document.querySelector("#motionToggle");
reduceMotionCB.checked = window.matchMedia("(prefers-reduced-motion: reduce)").matches;
reduceMotionCB.addEventListener("change", gsap.matchMediaRefresh); // force all matchMedia() stuff to revert and re-run

let breakPoint = 800;
let mm = gsap.matchMedia();

mm.add({
  isDesktop: `(min-width: ${breakPoint}px)`, // <- when ANY of these are true, the function below gets invoked
  isMobile: `(max-width: ${breakPoint - 1}px)`
}, (context) => {

  let {isDesktop, isMobile} = context.conditions;
  let reduceMotion = reduceMotionCB.checked; // if we weren't using a checkbox, we could just add another condition above: "(prefers-reduced-motion: reduce)"
  let tl = gsap.timeline({
    scrollTrigger: {
      trigger: ".gray",
      scrub: 1,
      end: "200%",
      pin: true
    }
  });
  tl.to(".box", { 
    scale: reduceMotion ? 1.1 : 2
  }).to(".box", { 
    scale: 1 
  });

  if (!reduceMotion) { // don't rotate the box if reduced motion was requested
    gsap.to(".box", {
      rotation: 360,
      ease: "none",
      duration: 5,
      repeat: -1
    });
  }

  gsap.set(".box", {
    innerText: isDesktop ? "Desktop" : "Mobile",

  });

  // optionally return a cleanup function
  return () => console.log("cleanup");
});

```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

[More information in this CSS tricks article](https://css-tricks.com/empathetic-animation/)

## Do I need to use gsap.context()?[​](#do-i-need-to-use-gsapcontext "Direct link to Do I need to use gsap.context()?")

Nope! Internally, gsap.matchMedia() creates a [gsap.context()](https://gsap.com/docs/v3/GSAP/gsap.context\(\)), so it would be redundant and completely unnecessary to use both. Think of gsap.matchMedia() like a specialized wrapper around [gsap.context()](https://gsap.com/docs/v3/GSAP/gsap.context\(\)). So when you call `revert()` on the gsap.matchMedia() object, it's the same thing as calling it on the [gsap.context()](https://gsap.com/docs/v3/GSAP/gsap.context\(\)).

## Examples[​](#examples "Direct link to Examples")

See the [CodePen Collection](https://codepen.io/collection/vBebgJ)

### Mobile device doesn't seem to work?[​](#mobile-device-doesnt-seem-to-work "Direct link to Mobile device doesn't seem to work?")

Try adding this in your `<head></head>`:

```
<meta name="viewport" content="width=device-width, initial-scale=1" />
```

gsap.matchMedia() was added in GSAP **3.11.0.**

---

*This documentation was extracted from the database for URLs containing 'gsap'*
