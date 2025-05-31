# lockedAxis | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/lockedAxis](https://gsap.com/docs/v3/Plugins/Draggable/lockedAxis)  
**Last Updated:** 2025-05-23T00:29:19.407Z  
**Extracted:** 2025-05-31 16:56:03

---

# lockedAxis | GSAP | Docs & Learning

The axis along which movement is locked during that particular drag.

_Boolean_ - The axis along which movement is locked (either `"x"` or `"y"`). For example, if `lockAxis` is `true` on a Draggable of `type: "x,y"`, and the user starts dragging horizontally, `lockedAxis` would be `"y"` because vertical movement won't be allowed during that drag. The `lockedAxis` property isn't set immediately upon press - the Draggable must wait to see which direction the user drags first. You can define a `onLockAxis` callback if you'd like to be notified when the axis gets locked.

`lockedAxis` is also populated on touch-enabled devices when you have a Draggable whose type only permits it to drag along one axis (like `type: "x"`, `type: "y"`, `type: "left"`, or `type: "top"`) and the user touch-drags and the Draggable determines the direction, either allowing native touch-scrolling or Draggable-induced dragging.

```
Draggable.create("#yourID", {  type: "x,y",  lockAxis: true,  onLockAxis: function () {    console.log("locked axis: " + this.lockedAxis);  },});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
