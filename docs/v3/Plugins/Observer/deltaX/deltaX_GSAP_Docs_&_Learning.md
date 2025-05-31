# deltaX | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Observer/deltaX](https://gsap.com/docs/v3/Plugins/Observer/deltaX)  
**Last Updated:** 2025-05-23T00:31:54.523Z  
**Extracted:** 2025-05-31 16:56:03

---

# deltaX | GSAP | Docs & Learning

### deltaX : Number

The amount of change (in pixels) horizontally since the last time a callback was fired on that axis. For example, `onChangeX` or `onRight`

### Details[​](#details "Direct link to Details")

The amount of change (in pixels) horizontally since the last time a callback was fired on that axis. For example, `onChangeX` or `onRight`

This is only affected by the event types that the Observer is watching. So, for example, `type: "wheel,touch"` would track the delta based on wheel and touch events (not pointer or scroll). By default, touch and pointer events are only tracked **while pressing/dragging** but if you define an `onMove` (which is mapped to "pointermove"/"mousemove" events), it'll be tracked during any movement while hovering over the target.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
