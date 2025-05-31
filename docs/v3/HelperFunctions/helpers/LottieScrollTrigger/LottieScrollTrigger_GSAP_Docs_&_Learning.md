# LottieScrollTrigger | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/LottieScrollTrigger](https://gsap.com/docs/v3/HelperFunctions/helpers/LottieScrollTrigger)  
**Last Updated:** 2025-05-23T00:19:29.540Z  
**Extracted:** 2025-05-31 16:56:03

---

# LottieScrollTrigger | GSAP | Docs & Learning

## Hook a Lottie animation up to ScrollTrigger

If you create an animation in After Effects and export it using [Lottie](https://airbnb.io/lottie/), you can hook it up to the scroll position with this handy function so that as the user scrolls, the animation progresses:

```
function LottieScrollTrigger(vars) {  let playhead = { frame: 0 },    target = gsap.utils.toArray(vars.target)[0],    speeds = { slow: "+=2000", medium: "+=1000", fast: "+=500" },    st = {      trigger: target,      pin: true,      start: "top top",      end: speeds[vars.speed] || "+=1000",      scrub: 1,    },    ctx = gsap.context && gsap.context(),    animation = lottie.loadAnimation({      container: target,      renderer: vars.renderer || "svg",      loop: false,      autoplay: false,      path: vars.path,      rendererSettings: vars.rendererSettings || {        preserveAspectRatio: "xMidYMid slice",      },    });  for (let p in vars) {    // let users override the ScrollTrigger defaults    st[p] = vars[p];  }  animation.addEventListener("DOMLoaded", function () {    let createTween = function () {      animation.frameTween = gsap.to(playhead, {        frame: animation.totalFrames - 1,        ease: "none",        onUpdate: () => animation.goToAndStop(playhead.frame, true),        scrollTrigger: st,      });      return () => animation.destroy && animation.destroy();    };    ctx && ctx.add ? ctx.add(createTween) : createTween();    // in case there are any other ScrollTriggers on the page and the loading of this Lottie asset caused layout changes    ScrollTrigger.sort();    ScrollTrigger.refresh();  });  return animation;}
```

### Usage[​](#usage "Direct link to Usage")

```
LottieScrollTrigger({  target: "#animationWindow",  path: "https://assets.codepen.io/35984/tapered_hello.json",  speed: "medium",  scrub: 2, // seconds it takes for the playhead to "catch up"  // you can also add ANY ScrollTrigger values here too, like trigger, start, end, onEnter, onLeave, onUpdate, etc. See /docs/v3/Plugins/ScrollTrigger});
```

**DEMO**

#### loading...

  CodePen Embed - LottieScrollTrigger  

```
<div id="animationWindow">
</div>


```

```
body {
 background-color: #0e100f;
overflow-x: hidden;
}

body,
html {
 height: 100%;
 width: 100%;
 margin: 0;
 padding: 0;
}

#animationWindow {
 width: 90vw;
 left: 5vw;
}

path {
 stroke: #0ae448;
}

```

```
LottieScrollTrigger({
 target: "#animationWindow",
 path: "https://assets.codepen.io/35984/tapered_hello.json",
 speed: "medium",
 scrub: 2 // seconds it takes for the playhead to "catch up"
 // you can also add ANY ScrollTrigger values here too, like trigger, start, end, onEnter, onLeave, onUpdate, etc. See https://greensock.com/docs/v3/Plugins/ScrollTrigger
 // you can pass in a "timeline" that has existing animations in it, and LottieScrollTrigger will play that alongside the Lottie animation
 // you can pass a startFrameOffset and/or endFrameOffset to cause the playhead to start/end at a different frame. 
});

function LottieScrollTrigger(vars) {
  let playhead = { frame: vars.startFrameOffset || 0 },
    target = gsap.utils.toArray(vars.target)[0],
    speeds = { slow: "+=2000", medium: "+=1000", fast: "+=500" },
    st = {
      trigger: target,
      pin: true,
      start: "top top",
      end: speeds[vars.speed] || "+=1000",
      scrub: 1
    },
    ctx = gsap.context && gsap.context(),
    animation = lottie.loadAnimation({
      container: target,
      renderer: vars.renderer || "svg",
      loop: false,
      autoplay: false,
      path: vars.path,
      rendererSettings: vars.rendererSettings || {
        preserveAspectRatio: "xMidYMid slice"
      }
    }),
    frameAnimation;
  for (let p in vars) {
    // let users override the ScrollTrigger defaults
    st[p] = vars[p];
  }
  frameAnimation = vars.timeline || gsap.timeline({ scrollTrigger: st });
  if (vars.timeline && !vars.timeline.vars.scrollTrigger) {
    // if the user passed in a timeline that didn't have a ScrollTrigger attached, create one.
    st.animation = frameAnimation;
    ScrollTrigger.create(st);
  }
  animation.addEventListener("DOMLoaded", function () {
    let createTween = function () {
      animation.goToAndStop(playhead.frame, true);
      frameAnimation.to(playhead, {
          frame: animation.totalFrames - 1 - (vars.endFrameOffset || 0),
          ease: "none",
          duration: frameAnimation.duration() || 1,
          onUpdate: () => {
            animation.goToAndStop(playhead.frame, true);
          }
        }, vars.sequence ? ">" : 0);
      return () => animation.destroy && animation.destroy();
    };
    ctx && ctx.add ? ctx.add(createTween) : createTween();
    // in case there are any other ScrollTriggers on the page and the loading of this Lottie asset caused layout changes
    ScrollTrigger.sort();
    ScrollTrigger.refresh();
  });
  animation.frameAnimation = frameAnimation;
  return animation;
}
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

Special thanks to Chris Gannon for his work on a [tool](https://github.com/chrisgannon/ScrollLottie) that inspired this.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
