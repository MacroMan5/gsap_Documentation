# removePause | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/removePause()](https://gsap.com/docs/v3/GSAP/Timeline/removePause())  
**Last Updated:** 2025-05-23T00:26:07.727Z  
**Extracted:** 2025-05-31 16:56:03

---

# removePause | GSAP | Docs & Learning

Removes the pause from a specific position which was added to the timeline via [`addPause()`](https://gsap.com/docs/v3/GSAP/Timeline/addPause\(\)).

```
var tl = gsap.timeline();tl.to(obj, { duration: 1, x: 100 });//added at time of 1tl.addPause();//another animationtl.to(obj, { duration: 1, opacity: 0 });//later on remove the pausetl.removePause(1);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
