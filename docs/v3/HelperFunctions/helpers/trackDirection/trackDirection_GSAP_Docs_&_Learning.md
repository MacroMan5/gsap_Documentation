# trackDirection | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/trackDirection](https://gsap.com/docs/v3/HelperFunctions/helpers/trackDirection)  
**Last Updated:** 2025-05-23T00:20:54.729Z  
**Extracted:** 2025-05-31 16:56:03

---

# trackDirection | GSAP | Docs & Learning

## Need an onReverse()? Track the playhead direction of any animation[​](#need-an-onreverse-track-the-playhead-direction-of-any-animation "Direct link to Need an onReverse()? Track the playhead direction of any animation")

If you find yourself needing an onReverse() callback (which doesn't exist) or a way to get notified when the playhead changes direction, this is a very useful helper function. What makes it special is that it works no matter how deeply-nested the animation is. Remember, the parent or parent's parent could get reversed or a negative timeScale which directly affects how the playhead sweeps across the descendants.

```
function trackDirection(value) {  typeof value !== "object" && (value = { onUpdate: value });  let prevTime = 0,    prevReversed = false,    anim = value.eventCallback ? value : value.animation,    onUpdate = value.onUpdate,    onToggle = value.onToggle;  return anim    ? anim.eventCallback(        "onUpdate",        trackDirection({ onUpdate: onUpdate, onToggle: onToggle })      )    : function () {        let time = this.totalTime(),          reversed = time < prevTime;        this.direction = reversed ? -1 : 1;        if (reversed !== prevReversed) {          onToggle && onToggle.call(this, this.direction);          prevReversed = reversed;        }        prevTime = time;        onUpdate && onUpdate.call(this, this.direction);      };}
```

## Usage[​](#usage "Direct link to Usage")

Choose from any of the following:

1.  Directly as a callback (it returns a function):
    
    ```
    gsap.to(... {onUpdate: trackDirection(), ...})
    ```
    
2.  Assigned to the animation:
    
    ```
    let tl = gsap.timeline();trackDirection(tl);
    ```
    

You can add configuration options (onToggle and/or onUpdate):

```
gsap.to(  ...{    x: 100,    onUpdate: trackDirection({      onToggle: (direction) => console.log("toggled direction to", direction),      onUpdate: (direction) => console.log("updated animation"),    }),  });
```

Or when assigned to the animation:

```
trackDirection({  animation: tl,  onToggle: (direction) => console.log("toggled direction to", direction),  onUpdate: (direction) => console.log("updated animation"),});
```

caution

since "direction" is set whenever the playhead changes position, it won't update immediately. For example, if you call tween.reverse() and then immediately check (before the next tick), tween.direction will still report as 1 because the playhead hasn't moved yet.

## Demo[​](#demo "Direct link to Demo")

#### loading...

  CodePen Embed - trackDirection() for GSAP  

```
<h1>trackDirection()</h1>
<p>Track the direction of any animation (tween or timeline) with this helper function. It's better than an onReverse() which purposely doesn't exist in the API; it works even when the animation is nested inside other animations which may themselves be reversed as well. </p><br>
<div class="box">Click to change direction</div>
<h2 class="direction"></h2>
```

```
body {
  text-align: center;
  padding: 10px 20px;
}

.box {
  width: 260px;
  height: 200px;
  background: linear-gradient(166.9deg, #0ae448 53.19%, #0085d0 107.69%), url(https://assets.codepen.io/16327/noise.png);
  background-blend-mode: color-dodge;
  text-align: center;
  font-size: 18px;
  display: inline-block;
  line-height: 200px;
  user-select: none;
  margin: 50px 0;
  border-radius: 20px;
  color: var(--color-just-black)
}
p {
  max-width: 800px;
  display: inline-block;
  text-align: left;
}
```

```
let tween = gsap.to(".box", {
  rotation: 360, 
  onUpdate: trackDirection(reportDirection), 
  ease: "power2.inOut", 
  duration: 5
});

function reportDirection() {
  document.querySelector(".direction").innerText = "direction: " + tween.direction;
}

// reverse on click
document.querySelector(".box").addEventListener("click", () => tween.reversed(!tween.reversed()));


/* 
Helper function that sets a "direction" property on any animation (tween or timeline) 
to -1 if the playhead is going backwards, or 1 if forward. It updates every time the playhead moves.
It must get applied to the onUpdate callback in one of the following ways: 

1) Directly as a callback (it returns a function):
gsap.to(... {onUpdate: trackDirection(), ...})

2) Assigned to the animation:
let tl = gsap.timeline();
trackDirection(tl);

You can add configuration options (onToggle and/or onUpdate):
gsap.to(... {
  x: 100, 
  onUpdate: trackDirection({
    onToggle: direction => console.log("toggled direction to", direction),
    onUpdate: direction => console.log("updated animation")
  })
});

Or when assigned to the animation:
trackDirection({
  animation: tl,
  onToggle: direction => console.log("toggled direction to", direction),
  onUpdate: direction => console.log("updated animation")
});

Caveat: since "direction" is set whenever the playhead changes position, it won't 
update immediately. For example, if you call tween.reverse() and then immediately check 
(before the next tick), tween.direction will still report as 1 because the playhead 
hasn't moved yet. 
*/
function trackDirection(value) {
  typeof(value) !== "object" && (value = {onUpdate: value});
  let prevTime = 0,
    prevReversed = false,
    anim = value.eventCallback ? value : value.animation,
    onUpdate = value.onUpdate,
    onToggle = value.onToggle;
  return anim ? anim.eventCallback("onUpdate", trackDirection({onUpdate: onUpdate, onToggle: onToggle})) : function() {
    let time = this.totalTime(),
      reversed = time < prevTime;
    this.direction = reversed ? -1 : 1;
    if (reversed !== prevReversed) {
      onToggle && onToggle.call(this, this.direction);
      prevReversed = reversed;
    }
    prevTime = time;
    onUpdate && onUpdate.call(this, this.direction);
  };
}
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
