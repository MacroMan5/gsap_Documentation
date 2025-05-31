# trigger | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/trigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger/trigger)  
**Last Updated:** 2025-05-23T00:34:01.326Z  
**Extracted:** 2025-05-31 16:56:03

---

# trigger | GSAP | Docs & Learning

\[read-only\] The trigger element (if one was defined). If selector text was used, like ".trigger", the `trigger` will be the element itself (not selector text). Also note that it is possible to define a ScrollTrigger _without_ a trigger because `start` and `end` can be **numbers** which are specific scroll values that aren't based on where a trigger element is in the document flow.

```
let st = ScrollTrigger.create({  trigger: ".trigger",  start: "top center",  end: "+=500",});console.log(st.trigger); // trigger element (not selector text)
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
