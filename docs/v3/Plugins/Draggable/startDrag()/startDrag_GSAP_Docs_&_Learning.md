# startDrag | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/startDrag()](https://gsap.com/docs/v3/Plugins/Draggable/startDrag())  
**Last Updated:** 2025-05-23T00:29:13.630Z  
**Extracted:** 2025-05-31 16:56:03

---

# startDrag | GSAP | Docs & Learning

### startDrag( event:Object, align:Boolean ) : void

Forces the Draggable to begin dragging.

#### Parameters

*   #### **event**: Object
    
    The mouse or touch or pointer event. It needs this in order to accurately measure distances and know where things start.
    
*   #### **align**: Boolean
    
    If the target element isn't on top of the pointer (according to the supplied event), setting `align` to `true` will move it there immediately.
    

### Details[​](#details "Direct link to Details")

This is rarely used, but you may force the Draggable to begin dragging by calling `startDrag()` and passing it the original mouse/touch/pointer event that initiated things - this is necessary because Draggable must inspect that event for various information like `pageX`, `pageY`, `target`, etc. You cannot call `startDrag()` without passing that original event.

`startDrag()` is different than `enable()` in that `enable()` activates the Draggable instance so that it responds to user interaction whereas `startDrag()` actually begins dragging the element, as if the user clicked on it and started dragging.

A great place to learn more about working with mouse/touch/pointer events is [this article](https://developers.google.com/web/fundamentals/design-and-ux/input/touch/).

---

*This documentation was extracted from the database for URLs containing 'gsap'*
