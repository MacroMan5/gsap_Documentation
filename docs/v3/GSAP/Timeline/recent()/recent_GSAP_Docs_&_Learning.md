# recent | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/recent()](https://gsap.com/docs/v3/GSAP/Timeline/recent())  
**Last Updated:** 2025-05-23T00:25:46.631Z  
**Extracted:** 2025-05-31 16:56:03

---

# recent | GSAP | Docs & Learning

Returns the most recently added child tween, timeline, or callback regardless of its position in the timeline.

```
var tl = gsap.timeline();//very long tweentl.to(e1, { duration: 999, x: 100, repeat: 5 });//insert this tween at 0.5 seconds (toward the beginning of the timeline)tl.to(e2, { duration: 1, y: 200 }, 0.5);//inserts the new tween 3 seconds after the e2 tween which was added most recently.tl.to(e3, { duration: 1, scaleX: 2 }, tl.recent().endTime() + 3);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
