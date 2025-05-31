# gsap.globalTimeline() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.globalTimeline()](https://gsap.com/docs/v3/GSAP/gsap.globalTimeline())  
**Last Updated:** 2025-05-23T00:22:44.615Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.globalTimeline() | GSAP | Docs & Learning

`gsap.globalTimeline` is the root Timeline instance that drives everything in GSAP, making it a powerful way to affect all animations at once. Keep in mind, however, that [gsap.delayedCalls()](https://gsap.com/docs/v3/GSAP/gsap.delayedCall\(\)) are also technically tweens, so if you [pause()](https://gsap.com/docs/v3/GSAP/Timeline/pause\(\)) or [timeScale()](https://gsap.com/docs/v3/GSAP/Timeline/timeScale\(\)) the globalTimeline, it will affect delayedCalls() too. If you want to omit those, check out [gsap.exportRoot()](https://gsap.com/docs/v3/GSAP/gsap.exportRoot\(\)).

```
gsap.globalTimeline.timeScale(0.5); //plays at half-speedgsap.globalTimeline.timeScale(2); //plays twice the normal speedvar currentTimeScale = gsap.globalTimeline.timeScale(); //returns the current global timeScale
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
