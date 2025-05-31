# endRotation | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/endRotation](https://gsap.com/docs/v3/Plugins/Draggable/endRotation)  
**Last Updated:** 2025-05-23T00:28:57.522Z  
**Extracted:** 2025-05-31 16:56:03

---

# endRotation | GSAP | Docs & Learning

### endRotation : Number

\[read-only\] \[only applies to type:"rotation"\] The ending rotation of the Draggable instance which is calculated as soon as the mouse/touch is released after a drag, meaning you can use it to predict precisely where it'll land after a `inertia` flick.

### Details[​](#details "Direct link to Details")

_Number_ - \[only applies to `type: "rotation"` Draggable objects\] The ending rotation of the Draggable instance. `endRotation` gets populated immediately when the mouse (or touch) is released after dragging, even before tweening has completed. This makes it easy to predict exactly what angle the element will land at (useful for `inertia: true` Draggables where momentum gets applied and you want to predict where it'll land).

---

*This documentation was extracted from the database for URLs containing 'gsap'*
