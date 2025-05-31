# static-convertCoordinates | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.convertCoordinates()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.convertCoordinates())  
**Last Updated:** 2025-05-23T00:31:14.826Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-convertCoordinates | GSAP | Docs & Learning

## MotionPathPlugin.convertCoordinates

### MotionPathPlugin.convertCoordinates( fromElement:Element | window, toElement:Element | window, point:Object ) : Object (point or Matrix2D)

Converts a point from one element's local coordinates into where that point lines up in a different element's local coordinate system regardless of how many nested transforms are affecting the elements!

#### Parameters

*   #### **fromElement**: Element | window
    
    The element whose local coordinates serve as the **input**. The `point` (3rd parameter) is defined according to this element's local coordinates.
    
*   #### **toElement**: Element | window
    
    The element whose local coordinates serve as the **output**. In other words, the `point` will be converted into this element's local coordinate system. This should be an element reference (like myElem), not a selector string
    
*   #### **point**: Object
    
    \[optional\] An object with x and y properties like `{x:100, y:200}` that define the local coordinates in the `fromElement` that should be converted into the `toElement`'s local coordinates.
    

If a `point` parameter is provided, it will be converted and a new point is returned like `{x: 100, y: 200}` representing the converted coordinates in the `toElement`. If no `point` is provided, a **Matrix2D** object is returned so that you can use it to quickly convert ANY coordinates using its `apply()` method.

Converts a point from one element's local coordinates into where that point lines up in a different element's local coordinate system regardless of how many nested transforms are affecting the elements! For example, if an element is rotated and scaled inside a transformed container and the user clicks on it, you could convert the event's pageX and pageY coordinates into where that is in that nested element's coordinate system.

```
let fromElement = document.querySelector("#from"),  toElement = document.querySelector("#to"),  point = { x: 100, y: 0 },  convertedPoint = MotionPathPlugin.convertCoordinates(    fromElement,    toElement,    point  );// or if you want to convert multiple points, don't pass one to the function and it'll return a Matrix2Dlet matrix = MotionPathPlugin.convertCoordinates(fromElement, toElement), // no point parameter!  p1 = matrix.apply({ x: 100, y: 0 }),  p2 = matrix.apply({ x: 0, y: 200 }),  p3 = matrix.apply({ x: 50, y: 50 });
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
