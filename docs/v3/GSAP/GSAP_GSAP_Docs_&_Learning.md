# GSAP | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/](https://gsap.com/docs/v3/GSAP/)  
**Last Updated:** 2025-05-23T00:16:18.211Z  
**Extracted:** 2025-05-31 16:56:03

---

# GSAP | GSAP | Docs & Learning

Quick Start

or via a package manager like npm

```
import { gsap } from "gsap"
```

#### Minimal usage

```
// This is a Tweengsap.to(".box", { rotation: 27, x: 100, duration: 1 });// And this is a Timeline, containing three sequenced tweenslet tl = gsap.timeline();tl.to("#green", {duration: 1, x: 786})  .to("#blue", {duration: 2, x: 786})  .to("#orange", {duration: 1, x: 786})
```

The `gsap` object serves as the access point for most of GSAP's functionality. It's just a generic object with various methods and properties that create and control [Tweens](https://gsap.com/docs/v3/GSAP/Tween) and [Timelines](https://gsap.com/docs/v3/GSAP/Timeline), two of the most important concepts to understand.

Quick Overview

For a quick overview of the GSAP object, check out this video from the ["GSAP 3 Express" course](https://courses.snorkl.tv/courses/gsap-3-express?ref=44f484) by Snorkl.tv - one of the best ways to learn the basics.

   The GSAP Object from GreenSock on Vimeo

To get the most out of GSAP, it's crucial that you understand what Tweens and Timelines are:

### What's a Tween?[​](#whats-a-tween "Direct link to What's a Tween?")

A [Tween](https://gsap.com/docs/v3/GSAP/Tween) is what does all the animation work - think of it like a **high-performance property setter**. You feed in targets (the objects you want to animate), a duration, and any properties you want it to animate and then when the Tween's playhead moves to a new position, figures out what the property values should be at that point applies them accordingly.

#### Common methods for creating a Tween:[​](#common-methods-for-creating-a-tween "Direct link to Common methods for creating a Tween:")

*   [gsap.to()](https://gsap.com/docs/v3/GSAP/gsap.to\(\))
*   [gsap.from()](https://gsap.com/docs/v3/GSAP/gsap.from\(\))
*   [gsap.fromTo()](https://gsap.com/docs/v3/GSAP/gsap.fromTo\(\))

For simple animations (no fancy sequencing), the methods above are all you need! For example:

```
//rotate and move elements with a class of "box" ("x" is a shortcut for a translateX() transform) over the course of 1 second.gsap.to(".box", { rotation: 27, x: 100, duration: 1 });
```

#### loading...

  CodePen Embed - GSAP Basic Tween  

```
<div class="box gradient-green green"></div>
<div class="box gradient-purple purple"></div>
<div class="box gradient-blue blue"></div>
```

```
/* Global styles come from external css https://codepen.io/GreenSock/pen/xxmzBrw/fcaef74061bb7a76e5263dfc076c363e.css
 */
body {
  display: flex;
  align-items: center;
  justify-content: space-around;
  min-height: 100vh;
  flex-direction: column;
}
```

```
// target the element with a class of "green" - rotate and move TO 100px to the left over the course of 1 second. 
gsap.to(".green", {rotation: 360, x: 100, duration: 1});

// target the element with a class of "purple" - rotate and move FROM 100px to the left over the course of 1 second. 
gsap.from(".purple", {rotation: -360, x: -100, duration: 1});

// target the element with a class of "blue" - rotate and move FROM 100px to the left, TO 100px to the right over the course of 1 second. 
gsap.fromTo(".blue", {x: -100},{rotation: 360, x: 100, duration: 1});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

You can do basic sequencing by using the `delay` special property, but Timelines make sequencing and complex choreography much, much easier.

### What's a Timeline?[​](#whats-a-timeline "Direct link to What's a Timeline?")

A [Timeline](https://gsap.com/docs/v3/GSAP/Timeline) is a **container for Tweens.** It's the ultimate sequencing tool that lets you position animations in time wherever you want and then control the whole sequence easily with methods like [pause()](https://gsap.com/docs/v3/GSAP/Timeline/pause\(\)), [play()](https://gsap.com/docs/v3/GSAP/Timeline/play\(\)), [progress()](https://gsap.com/docs/v3/GSAP/Timeline/progress\(\)), [reverse()](https://gsap.com/docs/v3/GSAP/Timeline/reverse\(\)), [timeScale()](https://gsap.com/docs/v3/GSAP/Timeline/timeScale\(\)), etc.

Create as many Timelines as you want. You can even **nest them** which is fantastic for modularizing your animation code! Every animation (Tween and Timeline) gets placed onto a parent timeline (the [globalTimeline](https://gsap.com/docs/v3/GSAP/gsap.globalTimeline\(\)) by default). Moving a Timeline's playhead cascades down through its children so that the playheads stay aligned. A Timeline is purely about grouping things and coordinating time/playheads - it never actually sets properties on targets (Tweens handle that).

```
//all tweens run in direct successionlet tl = gsap.timeline();tl.to("#green", {duration: 1, x: 918})  .to("#blue", {duration: 2, x: 918})  .to("#orange", {duration: 1, x: 918})
```

#### Method for creating a Timeline:[​](#method-for-creating-a-timeline "Direct link to Method for creating a Timeline:")

*   [gsap.timeline()](https://gsap.com/docs/v3/GSAP/gsap.timeline\(\))

GSAP's API lets you control virtually anything on-the-fly, such as the playhead position, the [startTime](https://gsap.com/docs/v3/GSAP/Tween/startTime\(\)) of any child, even play/pause/reverse the timeline or alter the timeScale itself.

## Sequencing[​](#sequencing "Direct link to Sequencing")

First, create a Timeline:

```
var tl = gsap.timeline();
```

Then add a tween using one of the convenience methods - [to()](https://gsap.com/docs/v3/GSAP/Timeline/to\(\)), [from()](https://gsap.com/docs/v3/GSAP/Timeline/from\(\)), or [fromTo()](https://gsap.com/docs/v3/GSAP/Timeline/fromTo\(\)):

```
tl.to(".box", { duration: 2, x: 100, opacity: 0.5 });
```

Do that as many times as you want. Notice we're calling `.to()` **on the timeline instance** (the variable `tl` in this case), not the `gsap` object. This creates a tween and immediately puts it into that particular Timeline. `gsap.to()`, on the other hand, creates a standalone tween. By default, the animations will be sequenced one-after-the-other. You can even use method chaining to simplify your code like this:

```
//sequenced one-after-the-othertl.to(".box1", { duration: 2, x: 100 }) //notice that there's no semicolon!  .to(".box2", { duration: 1, y: 200 })  .to(".box3", { duration: 3, rotation: 360 });
```

#### loading...

  CodePen Embed - GSAP Basic Timeline  

```
<div class="box box1 green"></div>
<div class="box box2 orange"></div>
<div class="box box3 purple"></div>
```

```
/* Global styles come from external css https://codepen.io/GreenSock/pen/xxmzBrw */

body {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  min-height: 100vh;
  gap: 1rem;
}

.box {
  display: block;
}

.pink {
  background-color: pink;
}
```

```
var tl = gsap.timeline({delay: 2});
//sequenced one-after-the-other
tl.to(".box1", {duration: 2, rotation: -360})
  .to(".box2", {duration: 1, x: -100, ease: 'elastic.out'})
  .to(".box3", {duration: 2, rotation: 360, x: 100, ease: 'expo.out'});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

info

The whole GSAP platform is object-oriented and you could create individual tween instances with [gsap.to()](https://gsap.com/docs/v3/GSAP/gsap.to\(\)), for example, and then [timeline.add()](https://gsap.com/docs/v3/GSAP/Timeline/add\(\)) each one but it's just easier to call .to(), .from(), or .fromTo() directly on the Timeline instance to do the same thing in fewer steps.

## Positioning[​](#positioning "Direct link to Positioning")

Define **exactly** where you want your animations to be placed into the timeline by using the optional [position parameter](https://gsap.com/resources/position-parameter/). A number indicates an absolute time (in seconds), or a string with a `"+="` or `"-="` prefix indicates an offset relative to the END of the timeline. For example, `"+=2"` would be 2 seconds after the end, creating a 2-second gap. `"-=2"` would create a 2-second overlap.

```
//starts at EXACTLY .5 seconds from the start of the Timeline:let tl = gsap.timeline();tl.to("#green", {duration: 1, x: 918}, .5)  .to("#blue", {duration: 1, x: 918}, "-=0.75") //overlaps by 0.75 seconds  .to("#orange", {duration: 1, x: 918}, "+=1") //adds a 1-second gap before
```

### Labels[​](#labels "Direct link to Labels")

Use labels to mark certain spots on the timeline so that you can place animations there or navigate there during playback.

```
//tweens are inserted at and relative to a label's positionlet tl = gsap.timeline();tl.to("#green", {duration: 1, x: 918})  //add blueSpin label 1 second after end of timeline  .add("blueSpin", "+=1")  //add tween at blueSpin label  .to("#blue", {duration: 1, x: 918, rotation: 360}, "blueSpin")  //insert tween 0.5 seconds after blueSpin label  .to("#orange", {duration: 1, x: 918, rotation: 360}, "blueSpin+=0.5");
```

```
//add a label at exactly 3 secondstl.addLabel("step2", 3)//then later, we can seek() to that spot:tl.seek("step2");
```

## Control methods[​](#control-methods "Direct link to Control methods")

[Tween](https://gsap.com/docs/v3/GSAP/Tween) and [Timeline](https://gsap.com/docs/v3/GSAP/Timeline) both extend an Animation class that exposes a myriad of useful methods and properties. Here are some of the most frequently used:

#### loading...

  CodePen Embed - Basic Control Methods  

```

<div class="container">
  <div class="flair flair--25"></div>
  <div class="nav light">
  <button id="play">play()</button>
  <button id="pause">pause()</button>
  <button id="resume">resume()</button>
  <button id="reverse">reverse()</button>
  <button id="restart">restart()</button>
</div>
</div>
```

```
/* Global styles come from external css https://codepen.io/GreenSock/pen/gOWxmWG.css*/

body {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  flex-direction: column;
}

button {
  text-transform: none;
  margin: 0.25rem;
}

.nav.light {
  padding-top: 2rem;
  background-color: transparent;
  display: flex;
  flex-wrap: wrap;
  justify-content: center
}
```

```
let nav = document.querySelector('.nav')

let tween = gsap.to(".flair", {
  duration: 2, 
  x: () => nav.offsetWidth, // animate by the px width of the nav
  xPercent: -100, // offset by the width of the box
  rotation: 360, 
  ease: "none", 
  paused: true
});

// click handlers for controlling the tween instance...
document.querySelector("#play").onclick = () => tween.play();
document.querySelector("#pause").onclick = () => tween.pause();
document.querySelector("#resume").onclick = () => tween.resume();
document.querySelector("#reverse").onclick = () => tween.reverse();
document.querySelector("#restart").onclick = () => tween.restart();
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

Reference the Tween or Timeline instance with a variable, and then control it whenever you want:

```
//you only need to create a variable if you want to control it later...var tween = gsap.to(...);var tl = gsap.timeline(); //"tl" short for timelinetl.to(...).to(...); //add animations.//now we can control them...tween.pause();tween.timeScale(2); //double speedtl.seek(3); //jump to 3 seconds intl.progress(0.5); //halfway through...
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
