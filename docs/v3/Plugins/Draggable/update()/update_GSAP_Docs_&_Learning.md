# update | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/update()](https://gsap.com/docs/v3/Plugins/Draggable/update())  
**Last Updated:** 2025-05-23T00:29:20.233Z  
**Extracted:** 2025-05-31 16:56:03

---

# update | GSAP | Docs & Learning

### update( applyBounds:Boolean, sticky:Boolean ) : Draggable

Updates the Draggable's x/y properties to reflect the target element's current position.

#### Parameters

*   #### **applyBounds**: Boolean
    
    (default = `false`) - if `true`, the Draggable's `applyBounds()` method will be called as well so that bounds are enforced (this takes more processing, though).
    
*   #### **sticky**: Boolean
    
    If `true`, the coordinates will be updated so that the Draggable "sticks" to the pointer which can be very helpful when reparenting an element. Otherwise, the element's positioning would naturally change when being nested into a different element.
    

### Returns : Draggable[​](#returns--draggable "Direct link to Returns : Draggable")

The Draggable instance itself (to make chaining possible).

### Details[​](#details "Direct link to Details")

Updates the Draggable's `x` and `y` properties to reflect the target element's current position. This can be useful if, for example, you manually change or tween the element's position, but then you want to make sure the Draggable's `x` and `y` reflect those changes. You could even point a tween's `onUpdate` to the Draggable's update method to ensure things are synchronized throughout a tween. Setting sticky to true can be helpful if you're re-parenting the target because it acts like it "sticks" to the pointer (otherwise, reparenting would naturally cause the position to change).

---

*This documentation was extracted from the database for URLs containing 'gsap'*
