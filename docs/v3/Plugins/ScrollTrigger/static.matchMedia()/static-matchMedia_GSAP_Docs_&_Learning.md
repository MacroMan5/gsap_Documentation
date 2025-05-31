# static-matchMedia | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.matchMedia()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.matchMedia())  
**Last Updated:** 2025-05-23T00:33:10.806Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-matchMedia | GSAP | Docs & Learning

## ScrollTrigger.matchMedia

### ScrollTrigger.matchMedia( vars:Object )

\[DEPRECATED\] Allows you to set up ScrollTriggers that only apply to certain viewport sizes (using media queries).

#### Parameters

*   #### **vars**: Object
    
    A configuration object containing a key for each media query, like `{"(min-width: 800px)": function() { ... }, "(max-width: 799px)": function() { ... }}`. A special `"all"` key can be used for ScrollTriggers that should persist.
    

Allows you to set up ScrollTriggers that only apply to certain viewport sizes (using media queries). It's surprisingly simple, actually - you pass in a configuration object with a key for each media query like "(min-width: 800px)" and an associated function that should run when that media query matches. Do all your setup tasks inside that function. Any ScrollTriggers that are created inside that function are automatically reverted and killed when that media query no longer matches! If the ScrollTrigger has an animation associated with it, that will also be reverted and killed.

Detailed Walkthrough

   Understanding ScrollTrigger.matchMedia() from GreenSock on Vimeo

_Without_ matchMedia(), you would need to:

*   Manually set up your own [window.matchMedia()](https://developer.mozilla.org/en-US/docs/Web/API/MediaQueryList#Examples) functionality, handlers, etc.
*   Manually [kill()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/kill\(\)) each ScrollTrigger that doesn't apply to the new size. That means either keeping track of them in an Array or using [ScrollTrigger.getAll()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.getAll\(\)).
*   Make sure things get reverted to their pre-pinned, pre-ScrollTrigger state before creating new ScrollTriggers so that they aren't contaminated. For example, if you had something pinned, it must get unpinned and put back into the normal document flow so that your CSS rules affect it properly.

But with `ScrollTrigger.matchMedia()`, it handles most of that automatically.

Each key in the configuration object is exactly the kind of rule you'd pass into the native [window.matchMedia()](https://developer.mozilla.org/en-US/docs/Web/API/MediaQueryList#Examples).

Each media query's function will get called whenever it becomes active (matches). So if a user resizes the browser past the breakpoint and back again multiple times, the function would get called that many times. Keep in mind that when the media query becomes inactive (not matching anymore), all of the associated ScrollTriggers get reverted and killed, so you don't need to worry about them building up.

## Simple structure[​](#simple-structure "Direct link to Simple structure")

```
ScrollTrigger.matchMedia({  // large  "(min-width: 960px)": function () {    // setup animations and ScrollTriggers for screens 960px wide or greater...    // These ScrollTriggers will be reverted/killed when the media query doesn't match anymore.  },  // medium  "(min-width: 600px) and (max-width: 959px)": function () {    // The ScrollTriggers created inside these functions are segregated and get    // reverted/killed when the media query doesn't match anymore.  },  // small  "(max-width: 599px)": function () {    // The ScrollTriggers created inside these functions are segregated and get    // reverted/killed when the media query doesn't match anymore.  },  // all  all: function () {    // ScrollTriggers created here aren't associated with a particular media query,    // so they persist.  },});
```

## Demo[​](#demo "Direct link to Demo")

#### loading...

  CodePen Embed - ScrollTrigger.matchMedia() Demo  

```

  <h1>ScrollTrigger.matchMedia() Demo</h1>
  <h2>DEPRECATED IN 3.11 IN FAVOUR OF <a href="https://greensock.com/docs/v3/GSAP/gsap.matchMedia()">GSAP.MATCHMEDIA</a></h2>

<section class="gray">
  <p>When the viewport is less than 800px, the "Mobile" div will animate. Otherwise, the "Desktop" one will.</p>
  <div class="mobile">Mobile</div>
  <div class="desktop">Desktop</div>
</section>

<section class="bottom">
  <p><strong>Pretty cool, right?</strong></p>
  <p>Resize your screen. 800px is the break point. It's all dynamic!</p>
  <p>Check out <a href="https://greensock.com/scrolltrigger">ScrollTrigger</a> today. </p>
</section>
```

```
body {
  text-align: center;
}
h1 {
  margin: 0;
  padding: 35px 10px;
  font-size: 40px;
  font-weight: 400;
}

.gray {
  width: 100%;
  height: 100vh;
}
.mobile, .desktop {
  width: 200px;
  height: 100px;
  background: var(--color-lilac);
  position: absolute;
  z-index: 0;
  left: 30%;
  top: 50%;
  transform: translate3d(-50%, -50%, 0);
  text-align: center;
  font-size: 1.5em;
  font-weight: 400;
  line-height: 100px;
  color: var(--color-just-black);
}
.desktop {
  left: 70%;
  background-color: var(--color-shockingly-green);
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
  font-size: 1.5em;
  box-sizing: border-box;
}
```

```
gsap.registerPlugin(ScrollTrigger);

// if there are objects that may get inline styles added (like via tweens) that should get reverted, use ScrollTrigger.saveStyles() initially so that the current inline styles are saved for later reversion. It's not always necessary, but it goes well with ScrollTrigger.matchMedia() so we figured it'd make sense to show it here (it's not needed in this demo)
ScrollTrigger.saveStyles(".mobile, .desktop");

/*** Different ScrollTrigger setups for various screen sizes (media queries) ***/
ScrollTrigger.matchMedia({
  
  // desktop
  "(min-width: 800px)": function() {
    // setup animations and ScrollTriggers for screens over 800px wide (desktop) here...
    // ScrollTriggers will be reverted/killed when the media query doesn't match anymore.
    let tl = gsap.timeline({
          scrollTrigger: {
          trigger: ".gray",
          scrub: 1,
          end: "200%",
          pin: true
        }
      });
    tl.to(".desktop", {scale: 2, rotation: 360})
      .to(".desktop", {scale: 1});
  }, 
  
  // mobile
  "(max-width: 799px)": function() {
    // Any ScrollTriggers created inside these functions are segregated and get
    // reverted/killed when the media query doesn't match anymore. 
    let tl = gsap.timeline({ 
        scrollTrigger:{
          trigger: ".gray",
          scrub: 1,
          end: "200%",
          pin: true
        }
      });
    tl.to(".mobile", {scale: 2, rotation: 360})
      .to(".mobile", {scale: 1});
  }, 
  
  // all 
  "all": function() {
    // ScrollTriggers created here aren't associated with a particular media query,
    // so they persist.
  }
  
});


```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

tip

You can also use [ScrollTrigger.saveStyles()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.saveStyles\(\)) to record the current inline styles of elements that may be affected by animations later. Then, whenever ScrollTrigger reverts things internally for that media query, it will revert the inline styles accordingly. For example, if your element starts with no inline styles but then you animate the opacity and "x" position, the element will have "opacity" and "transform" inline styles (even if you rewind the tween) which would override other CSS rules. This solves that issue.

## Example code[​](#example-code "Direct link to Example code")

```
// record the initial inline CSS for these elements so that ScrollTrigger can revert them even if animations add inline styles laterScrollTrigger.saveStyles(".panel, #logo"); // if you put this INSIDE one of the functions, it'll only revert the recorded elements when that media query no longer matches. You can use ScrollTrigger.saveStyles() in multiple places.ScrollTrigger.matchMedia({  // desktop  "(min-width: 800px)": function () {    gsap.to(".panel", {      xPercent: -100,      scrollTrigger: {        trigger: ".panel",        scrub: 1,        pin: true,        end: "+=500",      },    });  },  // mobile  "(max-width: 799px)": function () {    gsap.to("#logo", {      scale: 0.5,      scrollTrigger: {        trigger: ".nav-bar",        start: "top top",        toggleActions: "play none reverse none",      },    });  },  // all  all: function () {    gsap.set(".photo", { opacity: 0 });    ScrollTrigger.batch(".photo", {      onEnter: (elements) =>        gsap.to(elements, { opacity: 1, stagger: 0.1, overwrite: true }),    });  },});
```

## Teardown function[​](#teardown-function "Direct link to Teardown function")

You can \[optionally\] **return a function** which will be called when that breakpoint no longer matches so that you can do custom cleanup routines like killing other animations that aren't ScrollTrigger-related. For example:

```
ScrollTrigger.matchMedia({  // desktop  "(min-width: 800px)": function () {    // ScrollTrigger (this automatically gets killed when the breakpoint no longer matches...    gsap.to(".panel", {      xPercent: -100,      scrollTrigger: {        trigger: ".panel",        scrub: 1,        end: "+=500",      },    });    // other animations that aren't ScrollTrigger-related...    let tl = gsap.timeline();    tl.to(".box", { rotation: 360 }).to(".box", { y: 100 });    // THIS IS THE KEY! Return a function that'll get called when the breakpoint no longer matches so we can kill() the animation (or whatever)    return function () {      tl.kill();      // other cleanup code can go here.    };  },});
```

Remember, ScrollTrigger automatically kills all ScrollTriggers created inside the media query function when that media query no longer matches, so you only need a teardown function for things that aren't directly related to ScrollTriggers. The animation that is associated with a particular ScrollTrigger will be killed along with the ScrollTrigger when the media query no longer matches. Any (or all) of the media queries can return a function.

### Mobile device doesn't seem to work?[​](#mobile-device-doesnt-seem-to-work "Direct link to Mobile device doesn't seem to work?")

Try adding this in your :

```
<meta name="viewport" content="width=device-width, initial-scale=1">
```

ScrollTrigger.matchMedia() was added in GSAP **3.4.0.**The teardown return function capability was added in**3.5.0.**

---

*This documentation was extracted from the database for URLs containing 'gsap'*
