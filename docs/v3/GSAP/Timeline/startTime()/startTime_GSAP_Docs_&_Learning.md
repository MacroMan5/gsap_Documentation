# startTime | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/startTime()](https://gsap.com/docs/v3/GSAP/Timeline/startTime())  
**Last Updated:** 2025-05-23T00:27:07.917Z  
**Extracted:** 2025-05-31 16:56:03

---

# startTime | GSAP | Docs & Learning

Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.

Gets or sets the time at which the animation begins on its parent timeline (after any `delay` that was defined). For example, if a tween starts at exactly 3 seconds into the timeline on which it is placed, the tween's `startTime` would be 3.

The `startTime` may be automatically adjusted to make the timing appear seamless if the parent timeline's `smoothChildTiming` property is `true` and a timing-dependent change is made on-the-fly, like `reverse()` is called or `timeScale()` is changed, etc. See the documentation for the [`smoothChildTiming`](https://gsap.com/docs/v3/GSAP/Timeline/smoothChildTiming) property of timelines for more details.

This method serves as both a getter and setter. Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.

```
//gets current start timevar start = tl.startTime();//setstl.startTime(2);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
