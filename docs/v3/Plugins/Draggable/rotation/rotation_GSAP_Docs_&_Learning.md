# rotation | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/rotation](https://gsap.com/docs/v3/Plugins/Draggable/rotation)  
**Last Updated:** 2025-05-23T00:29:43.912Z  
**Extracted:** 2025-05-31 16:56:03

---

# rotation | GSAP | Docs & Learning

### rotation : Number

\[read-only\] \[only applies to `type: "rotation"`\] The current rotation (in degrees) of the Draggable instance.

### Details[​](#details "Direct link to Details")

_Number_ - \[only applies to `type: "rotation"`\] The current rotation (in degrees) of the Draggable instance. This is the rotation transform, as in the CSS `transform: rotate(...deg)`. This value is updated each time the Draggable is dragged interactively and during the momentum-based tween that Draggable applies when the user releases their mouse/touch, but if you manually change (or tween) the element's rotation you can force Draggable to look at the "real" value and record it to its own `x` property by calling the Draggable's `update()` method. Basically that re-synchronizes it. Again, this is not necessary unless other code (outside Draggable) alters the target element's position.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
