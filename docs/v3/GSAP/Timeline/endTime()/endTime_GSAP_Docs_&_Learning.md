# endTime | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/endTime()](https://gsap.com/docs/v3/GSAP/Timeline/endTime())  
**Last Updated:** 2025-05-23T00:26:12.737Z  
**Extracted:** 2025-05-31 16:56:03

---

# endTime | GSAP | Docs & Learning

The end time of the timeline according to its parent timeline.

Returns the time at which the animation will finish according to the parent timeline's local time. This does factor in the `timeScale`. For example:

```
var tl = gsap.timeline();//create a 1-second tweenvar tween = gsap.to(e, { duration: 1, x: 100 });//insert the tween at 0.5 seconds into the timelinetl.add(tween, 0.5);console.log(tween.endTime()); //1.5//double the speed of the tween, thus it'll finish in half the normal timetween.timeScale(2);console.log(tween.endTime()); //1
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
