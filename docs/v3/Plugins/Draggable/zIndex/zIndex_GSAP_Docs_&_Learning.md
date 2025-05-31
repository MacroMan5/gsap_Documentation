# zIndex | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/zIndex](https://gsap.com/docs/v3/Plugins/Draggable/zIndex)  
**Last Updated:** 2025-05-23T00:28:29.932Z  
**Extracted:** 2025-05-31 16:56:03

---

# zIndex | GSAP | Docs & Learning

### zIndex : Number

\[static\] The starting zIndex that gets applied by default when an element is pressed/touched (for positional types, like `"x,y"`, `"top,left"`, etc.

### Details[​](#details "Direct link to Details")

_Number_ - The starting `zIndex` that gets applied by default when an element is pressed/touched (for positional types, like `"x,y"`, `"top,left"`, etc. but not `"rotation"` or `"scroll"`) and this number gets incremented and applied to each new element that gets pressed/touched so that the stacking order looks correct (newly pressed objects rise to the top) unless `zIndexBoost: false` is set in a particular Draggable's `vars` parameter. You can set this `zIndex` to whatever you want, but `1000` is the default.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
