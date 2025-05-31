# static-timeSinceDrag | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/static.timeSinceDrag()](https://gsap.com/docs/v3/Plugins/Draggable/static.timeSinceDrag())  
**Last Updated:** 2025-05-23T00:29:18.733Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-timeSinceDrag | GSAP | Docs & Learning

The time (in seconds) since the last drag ended.

Returns the time (in seconds) that has elapsed since the last drag ended - this can be useful in situations where you want to skip certain actions if a drag just occurred. For example, imagine a draggable `<div>` with a bunch of child elements that have `onclick` handlers - if the user clicks on of those and drags the whole `<div>` and then releases, you might want to ignore that "click" because the user was intending to drag, not click (don't forget to set `dragClickables: true` in the Draggable):

```
$("#myDiv a").click(function(e) {    if (Draggable.timeSinceDrag() > 0.2) {        //do stuff, but not if the user just dragged within the last 0.2 seconds    }});
```

There is also a `timeSinceDrag()` instance method.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
