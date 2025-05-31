# scroll | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/scroll()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/scroll())  
**Last Updated:** 2025-05-23T00:34:32.816Z  
**Extracted:** 2025-05-31 16:56:03

---

# scroll | GSAP | Docs & Learning

If a parameter is provided, it'll act as a setter and return undefined. If no parameter is provided, it'll act as a getter and return the numeric scroll position on the appropriate axis (vertical by default)

Gets/Sets the scroll position of the associated scroller (numeric). Remember that a ScrollTrigger is EITHER linked to **vertical** OR **horizontal** scrolling, so scroll() only affects that direction.

```
let st = ScrollTrigger.create({  trigger: ".class",  scroller: ".container", // if no scroller is defined, the viewport (window) is used.  start: "top center",  end: "+=500",});// getlet position = st.scroll();// setst.scroll(100);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
