# endDrag | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/endDrag()](https://gsap.com/docs/v3/Plugins/Draggable/endDrag())  
**Last Updated:** 2025-05-23T00:28:47.409Z  
**Extracted:** 2025-05-31 16:56:03

---

# endDrag | GSAP | Docs & Learning

### endDrag( event:Object ) : void

You may force the Draggable to immediately stop interactively dragging by calling `endDrag()` and passing it the original mouse or touch event that initiated the stop - this is necessary because Draggable must inspect that event for various information like `pageX`, `pageY`, `target`, etc.

#### Parameters

*   #### **event**: Object
    
    A mouse or touch event.
    

### Details[​](#details "Direct link to Details")

You may force the Draggable to immediately stop interactively dragging by calling `endDrag()` and passing it the original mouse or touch event that initiated the stop - this is necessary because Draggable must inspect that event for various information like `pageX`, `pageY`, `target`, etc. You cannot call `endDrag()` without passing that original event.

`endDrag()` is different than `disable()` in that `disable()` completely shuts down the Draggable instance so that the user cannot initiate dragging anymore whereas `endDrag()` simply stops a drag-in-progress, acting like the user released their mouse/touch.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
