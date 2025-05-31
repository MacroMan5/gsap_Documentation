# velocityX | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Observer/velocityX](https://gsap.com/docs/v3/Plugins/Observer/velocityX)  
**Last Updated:** 2025-05-23T00:32:24.229Z  
**Extracted:** 2025-05-31 16:56:03

---

# velocityX | GSAP | Docs & Learning

### velocityX : Number

The horizontal velocity (in pixels per second).

### Details[​](#details "Direct link to Details")

The horizontal velocity (in pixels per second).

This is only affected by the event types that the Observer is watching. So, for example, `type: "wheel,touch"` would track the velocity based on wheel and touch events (not pointer or scroll). By default, touch and pointer events are only tracked **while pressing/dragging** but if you define an `onMove` (which is mapped to "pointermove"/"mousemove" events), it'll be tracked during any movement while hovering over the target.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
