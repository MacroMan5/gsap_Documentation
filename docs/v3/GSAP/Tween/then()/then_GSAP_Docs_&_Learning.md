# then | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Tween/then()](https://gsap.com/docs/v3/GSAP/Tween/then())  
**Last Updated:** 2025-05-23T00:24:54.932Z  
**Extracted:** 2025-05-31 16:56:03

---

# then | GSAP | Docs & Learning

Returns a promise so that you can uses promises to track when a tween or timeline is complete.

Some people prefer to use a [Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) instead of an `onComplete` callback - that's exactly what `then()` is for. It returns a `Promise` that will get resolved when the animation completes.

```
gsap.to(".class", {duration: 1, x: 100}).then(yourFunction).then(...);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
