# x | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/x](https://gsap.com/docs/v3/Plugins/Draggable/x)  
**Last Updated:** 2025-05-23T00:28:21.430Z  
**Extracted:** 2025-05-31 16:56:03

---

# x | GSAP | Docs & Learning

### x : Number

\[read-only\] The current x (horizontal) position of the Draggable instance.

### Details[​](#details "Direct link to Details")

_Number_ - The current `x` (horizontal) position of the Draggable instance. For a Draggable of `type: "x,y"`, it would be the `x` transform translation, as in the CSS `transform: translateX(...)`. For `type: "top,left"`, the Draggable's `x` would refer to the CSS `left` value that's applied. This is not the global coordinate - it is the inline CSS-related value applied to the element.

This value is updated each time the Draggable is dragged interactively and during the momentum-based tween that Draggable applies when the user releases their mouse/touch, but if you manually change (or tween) the element's position you can force Draggable to look at the "real" value and record it to its own `x` property by calling the Draggable's `update()` method. Basically that re-synchronizes it. Again, this is not necessary unless other code (outside Draggable) alters the target element's position.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
