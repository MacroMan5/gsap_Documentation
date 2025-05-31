# end | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/end](https://gsap.com/docs/v3/Plugins/ScrollTrigger/end)  
**Last Updated:** 2025-05-23T00:33:21.820Z  
**Extracted:** 2025-05-31 16:56:03

---

# end | GSAP | Docs & Learning

### .end : Number

\[read-only\] The ScrollTrigger's ending scroll position (numeric, in pixels).

### Details[​](#details "Direct link to Details")

\[read-only\] The ScrollTrigger's ending scroll position (numeric, in pixels). This value gets calculated when the ScrollTrigger is refreshed, so anytime the window/scroller gets resized it'll be recalculated.

For example, if the trigger element is 100px below the bottom of the viewport (out of view), and the ScrollTrigger's [vars](https://gsap.com/docs/v3/Plugins/ScrollTrigger/vars) had `end: "top bottom"`, then the ScrollTrigger's calculated `end` property would be 100 (meaning it'd have to scroll 100px to hit the ending point).

The ScrollTrigger's `start` and `end` properties will always be numeric and reflect the scroll position in pixels.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
