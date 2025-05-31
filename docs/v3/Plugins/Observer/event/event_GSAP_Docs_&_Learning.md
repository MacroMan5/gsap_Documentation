# event | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Observer/event](https://gsap.com/docs/v3/Plugins/Observer/event)  
**Last Updated:** 2025-05-23T00:32:04.936Z  
**Extracted:** 2025-05-31 16:56:03

---

# event | GSAP | Docs & Learning

### event : Event

The most recent Event object (could be a TouchEvent, PointerEvent, MouseEvent, WheelEvent, or ScrollEvent based on whatever `type` you define)

### Details[​](#details "Direct link to Details")

The most recent Event object (could be a TouchEvent, PointerEvent, MouseEvent, WheelEvent, or ScrollEvent based on whatever `type` you define). For example, if your Observer has `type: "touch,pointer"` and you press down and drag with your mouse, the `event` would be a PointerEvent or MouseEvent based on your browser/device. This allows you to get whatever information you need from that event like pageX, pageY, etc. For touch and pointer events, the event.clientX and event.clientY are automatically saved to the "x" and "y" properties of the Observer for convenience.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
