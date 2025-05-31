# velocityY | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Observer/velocityY](https://gsap.com/docs/v3/Plugins/Observer/velocityY)  
**Last Updated:** 2025-05-23T00:32:26.218Z  
**Extracted:** 2025-05-31 16:56:03

---

# velocityY | GSAP | Docs & Learning

### velocityY : Number

The vertical velocity (in pixels per second).

### Details[​](#details "Direct link to Details")

The vertical velocity (in pixels per second).

This is only affected by the event types that the Observer is watching. So, for example, `type: "wheel,touch"` would track the velocity based on wheel and touch events (not pointer or scroll). By default, touch and pointer events are only tracked **while pressing/dragging** but if you define an `onMove` (which is mapped to "pointermove"/"mousemove" events), it'll be tracked during any movement while hovering over the target.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
