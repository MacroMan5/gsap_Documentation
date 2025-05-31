# start | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/start](https://gsap.com/docs/v3/Plugins/ScrollTrigger/start)  
**Last Updated:** 2025-05-23T00:33:56.616Z  
**Extracted:** 2025-05-31 16:56:03

---

# start | GSAP | Docs & Learning

### start : Number

\[read-only\] The ScrollTrigger's starting scroll position (numeric, in pixels).

### Details[​](#details "Direct link to Details")

\[read-only\] The ScrollTrigger's starting scroll position (numeric, in pixels). This value gets calculated when the ScrollTrigger is refreshed, so anytime the window/scroller gets resized it'll be recalculated.

For example, if the trigger element is 100px below the bottom of the viewport (out of view), and the ScrollTrigger's [vars](https://gsap.com/docs/v3/Plugins/ScrollTrigger/vars) had `start: "top bottom"`, then the ScrollTrigger's calculated `start` property would be 100 (meaning it'd have to scroll 100px to hit the starting point).

The ScrollTrigger's `start` and `end` properties will always be numeric and reflect the scroll position in pixels.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
