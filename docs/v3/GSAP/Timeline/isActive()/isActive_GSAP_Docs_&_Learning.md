# isActive | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/isActive()](https://gsap.com/docs/v3/GSAP/Timeline/isActive())  
**Last Updated:** 2025-05-23T00:27:01.117Z  
**Extracted:** 2025-05-31 16:56:03

---

# isActive | GSAP | Docs & Learning

### isActive( ) : Boolean

Indicates whether or not the animation is currently active (meaning the virtual playhead is actively moving across this instance's time span and it is not paused, nor are any of its ancestor timelines).

### Returns : Boolean[​](#returns--boolean "Direct link to Returns : Boolean")

Returns a Boolean that indicates whether or not the timeline is currently active.

### Details[​](#details "Direct link to Details")

Indicates whether or not the animation is currently active (meaning the virtual playhead is actively moving across this instance's time span and it is not paused, nor are any of its ancestor timelines). So for example, if a timeline is in the middle of animating, it's active, but after it is finished (or before it begins), it is **not** active. If it is paused or if it is placed inside of a timeline that's paused (or if any of its ancestor timelines are paused), `isActive()` will return `false`. If the playhead is directly on top of the animation's start time (even if it hasn't rendered quite yet), that counts as "active".

You may also check the [`timeline.progress()`](https://gsap.com/docs/v3/GSAP/Timeline/progress\(\)) or [`timeline.totalProgress()`](https://gsap.com/docs/v3/GSAP/Timeline/totalProgress\(\)), but those don't take into consideration the paused state or the position of the parent timeline's playhead. The global timeline is always considered active.

In the demo below we use `isActive()` to make sure the tween can not have its direction changed while it is active. Click the **toggle tween direction** button repeatedly to see that clicks are ignored while the box is moving.

#### loading...

  CodePen Embed - check isActive()  

```
<h3>You can only toggle direction when the tween is not active</h3>
<div class="wrapper">
  <div class="box green"></div>
</div>
<button class="dark-grey-button club-demo-button" id="tweenBox">toggle direction (only when tween is not active)</button> 
```

```
body{display:flex;align-items:center;justify-content:center;min-height:100vh;flex-direction: column}

.wrapper {
  width:400px;
  height:100px;
  background:#313131;
  margin-bottom:10px;
  border-radius: 10px;
}

.box {
  width:100px;
  height:100px;
}

button {
  margin:10px 0;
  padding:10px;
}
```

```
var endX = 300;
var box = $(".box")[0];
var tween = gsap.to(box, {duration:2, x:endX, ease:"none"}).reverse();


$("#tweenBox").click(function(){
  if(!tween.isActive()){
    console.log(tween.reversed(), tween.paused())
    //only reverse the direction if the tween is not active
    tween.reversed(!tween.reversed())
  }
});

/* from the API documentation

isActive() indicates whether or not the animation is currently active (meaning the virtual playhead is actively moving across this instance's time span and it is not paused, nor are any of its ancestor timelines). So for example, if a tween is in the middle of tweening, it's active, but after it is finished (or before it begins), it is not active. If it is paused or if it is placed inside of a timeline that's paused (or if any of its ancestor timelines are paused), isActive() will return false. If the playhead is directly on top of the animation's start time (even if it hasn't rendered quite yet), that counts as "active".

*/
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
