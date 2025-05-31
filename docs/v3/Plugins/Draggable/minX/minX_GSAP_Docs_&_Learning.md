# minX | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/minX](https://gsap.com/docs/v3/Plugins/Draggable/minX)  
**Last Updated:** 2025-05-23T00:29:40.825Z  
**Extracted:** 2025-05-31 16:56:03

---

# minX | GSAP | Docs & Learning

### minX : Number

When bounds are applied, `minX` refers to the minimum "legal" horizontal property.

### Details[​](#details "Direct link to Details")

_Number_ - When bounds are `applied`, `minX` refers to the minimum "legal" value of the horizontal property (either `"x"` or `"left"`, depending on which type the Draggable is). This makes it easier to run your own custom logic inside the snap or callback function(s) if you so choose. So for a Draggable of `type: "x,y"`, `minX` would correlate with `x` transform translation, as in the CSS `transform: translateX(...)`. For `type: "top,left"`, the Draggable's `minX` would correlate with the CSS `left` value that's applied. This is not the global coordinate - it is the inline CSS-related value applied to the element.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
