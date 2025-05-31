# tween | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/tween](https://gsap.com/docs/v3/Plugins/Draggable/tween)  
**Last Updated:** 2025-05-23T00:29:58.610Z  
**Extracted:** 2025-05-31 16:56:03

---

# tween | GSAP | Docs & Learning

### tween : Tween

\[read-only\] The Tween instance that gets created as soon as the mouse (or touch) is released (when `inertia` is `true`). This allows you to check its `duration`, `.pause()` or `.resume()` it, change its `timeScale`, or whatever you want.

### Details[​](#details "Direct link to Details")

_Tween_ - The tween instance that gets created as soon as the mouse (or touch) is released (when `inertia` is `true`) - this allows you to check its `duration`, `pause()` it, `resume()` it, change its `timeScale`, or whatever you want. Keep in mind that a new tween is created each time the element is "thrown". You can easily get it when the user releases the mouse (or touch) by referencing `this.tween` inside the `onDragEnd` callback.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
