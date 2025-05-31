# gsap.to() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.to()](https://gsap.com/docs/v3/GSAP/gsap.to())  
**Last Updated:** 2025-05-23T00:22:46.013Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.to() | GSAP | Docs & Learning

### Returns : [Tween](https://gsap.com/docs/v3/GSAP/Tween)[​](#returns--tween "Direct link to returns--tween")

The most common type of animation is a **to()** tween because it allows you to define the **destination values** (and most people think in terms of animating **_to_** certain values):

```
// rotate and move elements with a class of "box"// ("x" is a shortcut for a translateX() transform) over the course of 1 second.gsap.to(".box", { rotation: 27, x: 100, duration: 1 });
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

GSAP figures out the current values automatically (you don't need to define starting values, though you can in a [fromTo()](https://gsap.com/docs/v3/GSAP/gsap.fromTo\(\)) tween). Since GSAP can animate **any** property of **any** object, you are _NOT_ limited to CSS properties or DOM objects. Go crazy. You may be surprised by how many things can be animated with GSAP and it "just works".

To control the Tween instance later, assign it to a variable (GSAP is conveniently object-oriented):

```
let tween = gsap.to(".class", {rotation: 360, duration: 5, ease: "elastic"});//now we can control it!tween.pause();tween.seek(2);tween.progress(0.5);tween.play();...
```

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

To simply fire off animations and let them run, there's no need to use variables. Tweens play immediately by default (though you can set a `delay` or `paused` value) and when they finish, they automatically dispose of themselves. Call `gsap.to()` as much as you want without worrying about cleanup.

Other types of tweens:

*   [from()](https://gsap.com/docs/v3/GSAP/gsap.from\(\)) - you define the **starting** values to animate _"from"_, GSAP uses the current values as the destinations (like a tween running backwards)
*   [fromTo()](https://gsap.com/docs/v3/GSAP/gsap.fromTo\(\)) - you define the **starting and ending** values.

## Parameters[​](#parameters "Direct link to Parameters")

1.  **targets** - the object(s) whose properties you want to animate. This can be selector text like `".class"`, `"#id"`, etc. (GSAP uses [`document.querySelectorAll()`](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll) internally) or it can be direct references to elements, generic objects, or even an array of objects.
2.  **vars** - an object containing all the properties/values you want to animate, along with any special properties like `ease`, `duration`, `delay`, or `onComplete` (listed below).

## Special Properties[​](#special-properties "Direct link to Special Properties")

Add any of these to your `vars` object to give your animation special powers:

*   #### callbackScope[](#callbackScope)
    
    The scope to be used for all of the callbacks (onStart, onUpdate, onComplete, etc.).
    
*   #### data[](#data)
    
    Assign arbitrary data to this property (a string, a reference to an object, whatever) and it gets attached to the tween instance itself so that you can reference it later like `yourTween.data`.
    
*   #### delay[](#delay)
    
    Amount of delay before the animation should begin (in seconds).
    
*   #### duration[](#duration)
    
    The duration of the animation (in seconds). Default: `0.5`
    
*   #### ease[](#ease)
    
    Controls the rate of change during the animation, giving it a specific feel. For example, `"elastic"` or `"strong.inOut"`. See the [Ease Visualizer](https://gsap.com/docs/v3/Eases) for a list of all of the options. `ease` can be a String (most common) or a function that accepts a progress value between 0 and 1 and returns a converted, similarly normalized value. Default: `"power1.out"`
    
*   #### id[](#id)
    
    Allows you to (optionally) assign a unique identifier to your tween instance so that you can find it later with `gsap.getById()` and it will show up in [GSDevTools](https://gsap.com/docs/v3/Plugins/GSDevTools/) with that id.
    
*   #### immediateRender[](#immediateRender)
    
     Normally a tween waits to render for the first time until the very next tick (update cycle) unless you specify a delay. Set `immediateRender: true` to force it to render immediately upon instantiation. Default: `false` for [to()](https://gsap.com/docs/v3/GSAP/gsap.to\(\)) tweens, `true` for [from()](https://gsap.com/docs/v3/GSAP/gsap.from\(\)) and [fromTo()](https://gsap.com/docs/v3/GSAP/gsap.fromTo\(\)) tweens or anything with a [scrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger) applied.
    
*   #### inherit[](#inherit)
    
    Normally tweens inherit from their parent timeline's `defaults` object (if one is defined), but you can disable this on a per-tween basis by setting `inherit: false`.
    
*   #### lazy[](#lazy)
    
    When a tween renders for the very first time and reads its starting values, GSAP will try to delay writing of values until the very end of the current "tick" which can improve performance because it avoids the read/write/read/write layout thrashing that browsers dislike. To disable lazy rendering for a particular tween, set `lazy: false`. In most cases, there's no need to set `lazy`. To learn more, watch [this video](https://www.youtube.com/watch?v=TMHJptqnDpU). Default: `true` (except for zero-duration tweens)
    
*   #### onComplete[](#onComplete)
    
    A function to call when the animation has completed
    
*   #### onCompleteParams[](#onCompleteParams)
    
    An Array of parameters to pass the onComplete function. For example, `gsap.to(".class", {x:100, onComplete:myFunction, onCompleteParams:["param1", "param2"]});`
    
*   #### onInterrupt[](#onInterrupt)
    
    A function to call when the animation is interrupted, meaning if/when the tween is killed before it completes. This could happen because its kill() method is called or due to overwriting.
    
*   #### onInterruptParams[](#onInterruptParams)
    
    An Array of parameters to pass the onInterrupt function. For example, `gsap.to(".class", {x:100, onInterrupt:myFunction, onInterruptParams:["param1", "param2"]});`.
    
*   #### onRepeat[](#onRepeat)
    
    A function to call each time the animation enters a new iteration cycle (repeats). Obviously this only occurs if you set a non-zero `repeat`.
    
*   #### onRepeatParams[](#onRepeatParams)
    
    An Array of parameters to pass the onRepeat function.
    
*   #### onReverseComplete[](#onReverseComplete)
    
    A function to call when the animation has reached its beginning again from the reverse direction (excluding repeats).
    
*   #### onReverseCompleteParams[](#onReverseCompleteParams)
    
    An Array of parameters to pass the onReverseComplete function.
    
*   #### onStart[](#onStart)
    
    A function to call when the animation begins (when its time changes from 0 to some other value which can happen more than once if the tween is restarted multiple times).
    
*   #### onStartParams[](#onStartParams)
    
    An Array of parameters to pass the onStart function.
    
*   #### onUpdate[](#onUpdate)
    
    A function to call every time the animation updates (on each "tick" that moves its playhead).
    
*   #### onUpdateParams[](#onUpdateParams)
    
    An Array of parameters to pass the onUpdate function.
    
*   #### overwrite[](#overwrite)
    
    If `true`, all tweens of the same targets will be killed immediately regardless of what properties they affect. If `"auto"`, when the tween renders for the first time it hunt down any conflicts in active animations (animating the same properties of the same targets) and kill **only those parts** of the other tweens. Non-conflicting parts remain intact. If `false`, no overwriting strategies will be employed. Default: `false`
    
*   #### paused[](#paused)
    
    If `true`, the animation will pause itself immediately upon creation. Default: `false`
    
*   #### repeat[](#repeat)
    
    How many times the animation should repeat. So `repeat: 1` would play a total of two iterations. Use -1 to repeat infinitely. Default: `0`
    
*   #### repeatDelay[](#repeatDelay)
    
    Amount of time to wait between repeats (in seconds). Default: `0`
    
*   #### repeatRefresh[](#repeatRefresh)
    
    Setting `repeatRefresh: true` causes a repeating tween to `invalidate()` and re-record its starting/ending values internally on each full iteration (not including yoyo's). This is useful when you use dynamic values (relative, random, or function-based). For example, `x: "random(-100, 100)"` would get a new random x value on each repeat. `duration`, `delay`, and `stagger` do **NOT** refresh.
    
*   #### reversed[](#reversed)
    
    If `true`, the animation will start out with its playhead reversed, meaning it will be oriented to move toward its start. Since the playhead begins at a time of 0 anyway, a reversed tween will _appear_ paused initially because its playhead cannot move backward past the start.
    
*   #### runBackwards[](#runBackwards)
    
    If `true`, the animation will invert its starting and ending values (this is what a [from()](https://gsap.com/docs/v3/GSAP/gsap.from\(\)) tween does internally), though the ease doesn't get flipped. In other words, you can make a `to()` tween into a `from()` by setting `runBackwards: true`.
    
*   #### stagger[](#stagger)
    
    If multiple targets are defined, you can easily [stagger](https://codepen.io/GreenSock/pen/938f5cd34818443c43af9ba2692137a5) the start times for each by setting a value like `stagger: 0.1` (for 0.1 seconds between each start time). Or you can get much more advanced staggers by using a stagger object. For more information, see [the stagger documentation](https://gsap.com/resources/getting-started/Staggers).
    
*   #### startAt[](#startAt)
    
    Defines starting values for any properties (even if they're not animating). For example, `startAt: {x: -100, opacity: 0}`
    
*   #### yoyo[](#yoyo)
    
    If `true`, every other `repeat` iteration will run in the opposite direction so that the tween appears to go back and forth. This has no affect on the `reversed` property though. So if `repeat` is `2` and `yoyo` is `false`, it will look like: start - 1 - 2 - 3 - 1 - 2 - 3 - 1 - 2 - 3 - end. But if `yoyo` is `true`, it will look like: start - 1 - 2 - 3 - 3 - 2 - 1 - 1 - 2 - 3 - end. Default: `false`
    
*   #### yoyoEase[](#yoyoEase)
    
    Allows you to alter the ease in the tween's `yoyo` phase. Set it to a specific ease like `"power2.in"` or set it to `true` to simply invert the tween's normal `ease`. Note: GSAP is smart enough to automatically set `yoyo: true` if you define any `yoyoEase`, so there's less code for you to write. Default: `false`
    
*   #### keyframes[](#keyframes)
    
    To animate the targets to various states, use `keyframes` - an array of vars objects that serve as `to()` tweens. For example, `keyframes: [{x:100, duration:1}, {y:100, duration:0.5}]`. All keyframes will be perfectly sequenced back-to-back, but you can define a `delay` value to add spacing between each step (or a negative delay would create an overlap). Keyframes are only to be used in `to()` tweens.
    

## Plugins[​](#plugins "Direct link to Plugins")

A plugin adds extra capabilities to GSAP's core. Some plugins make it easier to work with rendering libraries like PIXI.js or EaselJS while other plugins add superpowers like [morphing](https://gsap.com/docs/v3/Plugins/MorphSVGPlugin) SVG shapes, adding [drag and drop](https://gsap.com/docs/v3/Plugins/Draggable) functionality, etc. This allows the GSAP core to remain relatively small and lets you add features only when you need them. [See the full list of plugins here](https://gsap.com/docs/v3/Plugins).

## Function-based values[​](#function-based-values "Direct link to Function-based values")

Get incredibly dynamic animations by using a function for any value, and it will get called **once for each target** the first time the tween renders, and whatever is returned by that function will be used as the value. This can be very useful for applying conditional logic or randomizing things (though GSAP has baked-in randomizing capabilities too...scroll down for that).

```
gsap.to(".class", {  x: 100, //normal value  y: function(index, target, targets) { //function-based value    return index \* 50;  },  duration: 1});
```

The function is passed three parameters:

1.  index - the index of the target in the array. For example, if there are 3 `<div>` elements with the class ".box", and you `gsap.to(".box", ...)`, the function gets called 3 times (once for each target); the index would be `0` first, then `1`, and finally `2`.
2.  target - the target itself (the `<div>` element in this example)
3.  targets - the array of targets (same as `tween.targets()`)

## Random values[​](#random-values "Direct link to Random values")

Define random values as a string like `"random(-100, 100)"` for a range or like `"random([red, blue, green])"` for an array and GSAP will swap in a random value **for each target** accordingly! This makes advanced randomized effects simple. You can even have the random number rounded to the closest increment of any number! For example:

```
gsap.to(".class", {  // chooses a random number between -100 and 100  // for each target, rounding to the closest 5!  x: "random(-100, 100, 5)",});
```

Or use an array-like value and GSAP will randomly select one of those:

```
gsap.to(".class", {  x: "random([0, 100, 200, 500])", // randomly selects one of the values (0, 100, 200, or 500)});
```

There's also a [`gsap.utils.random()`](https://gsap.com/docs/v3/GSAP/UtilityMethods/random\(\)) function that you can use directly if you prefer.

## Relative values[​](#relative-values "Direct link to Relative values")

Use a`"+="` or `"-="` prefix to indicate a relative value. For example, `gsap.to(".class", {x:"-=20"});` will animate `x` 20 pixels **less than** whatever it is when the tween starts. `{x:"+=20"}` would **add** 20. To use a variable in a relative way, simply add the `"+="` or `"-="` prefix, like `{x: "+=" + yourVariable}`.

## Staggers[​](#staggers "Direct link to Staggers")

If multiple targets are defined, you can easily [stagger](https://codepen.io/GreenSock/pen/938f5cd34818443c43af9ba2692137a5) (offset) the start times for each by setting a value like `stagger: 0.1` (for 0.1 seconds between each start time).Or you can get much more advanced staggers by using a stagger object. For more information, see [the stagger documentation](https://gsap.com/resources/getting-started/Staggers).

## Sequencing[​](#sequencing "Direct link to Sequencing")

For basic sequencing, you could use a `delay` on each tween (like `gsap.to(".class", {`delay: 0.5, `duration: 1, x: 100})`), but we **strongly** recommended using a [`Timeline`](https://gsap.com/docs/v3/GSAP/Timeline) for all but the simplest sequencing tasks because it gives you much greater flexibility, especially when you're experimenting with timing. It allows you to append tweens one-after-the-other and then control the entire sequence as a whole. You can even have the tweens overlap as much as you want, nest timelines as deeply as you want, and much, much more.

Timelines have convenient [to()](https://gsap.com/docs/v3/GSAP/Timeline/to\(\)), [from()](https://gsap.com/docs/v3/GSAP/Timeline/from\(\)), and [fromTo()](https://gsap.com/docs/v3/GSAP/Timeline/fromTo\(\)) methods as well so you can very easily chain them together and build complex sequences:

```
let tl = gsap.timeline(); //create the timelinetl.to(".class1", { x: 100 }) //start sequencing  .to(".class2", { y: 100, ease: "elastic" })  .to(".class3", { rotation: 180 });
```

## Keyframes[​](#keyframes "Direct link to Keyframes")

If you find yourself animating the same target over and over again, you should definitely check out [Keyframes](https://gsap.com/resources/keyframes/) which can make your code much more concise. They also let you port animations over from CSS animations easily.

[Learn more about keyframes](https://gsap.com/resources/keyframes/)

## Callbacks[​](#callbacks "Direct link to Callbacks")

Callbacks are functions that are called after certain events happen in a tween or timeline like when they start, complete, repeat, reverse complete, or update. They can be very useful for debugging, keeping different parts of your project in sync, and many other things.

Callbacks and Callback scope

GSAP: Understanding Callbacks and Callback Scope - YouTube

To learn more about GSAP's callbacks, check out this video from the ["GSAP 3 Express" course](https://courses.snorkl.tv/courses/gsap3-beyond-the-basics?ref=44f484) by Snorkl.tv - one of the best ways to learn the basics of GSAP 3.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
