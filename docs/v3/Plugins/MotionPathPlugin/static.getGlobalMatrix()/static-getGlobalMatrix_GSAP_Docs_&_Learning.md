# static-getGlobalMatrix | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getGlobalMatrix()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getGlobalMatrix())  
**Last Updated:** 2025-05-23T00:31:22.454Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-getGlobalMatrix | GSAP | Docs & Learning

## MotionPathPlugin.getGlobalMatrix

### MotionPathPlugin.getGlobalMatrix( element:Element, inverse:Boolean, adjustGOffset:Boolean ) : Matrix2D

Gets the Matrix2D that would be used to convert the element's local coordinate space into the global coordinate space. So, for example, if you take a point `{x:0, y:0}` and `apply()` the matrix to it, the resulting point would be the viewport coordinates of that element's top left corner.

#### Parameters

*   #### **element**: Element
    
    The element whose global matrix should be returned. This should be an element reference (like myElem), not a selector string (like "#myElem").
    
*   #### **inverse**: Boolean
    
    \[optional\] if `true`, the inverse of the matrix will be returned, meaning that it'll produce the exact opposite transformation (like calling inverse() on the matrix)
    
*   #### **adjustGOffset**: Boolean
    
    \[optional\] if `true`, the x/y offsets of `<g>` elements will be ignored (they behave differently than most other elements).
    

Gets the Matrix2D that would be used to convert the element's local coordinate space into the global coordinate space. So, for example, if you take a point `{x:0, y:0}` and apply the matrix to it, the resulting point would be the window/viewport coordinates of that element's top left corner.

A Matrix2D is just an object with `a`, `b`, `c`, `d`, `e`, and `f` properties representing a 2D transformation matrix (very similar to an [SVGMatrix](https://developer.mozilla.org/en-US/docs/Web/API/SVGMatrix)). It contains all rotation, scale, skew, and x/y translation data and it's useful for converting between coordinate spaces. It has an `apply()` method that accepts a point (like `matrix.apply({x:0, y:100})`) and returns a new point with the matrix transforms applied.

```
let matrix = MotionPathPlugin.getGlobalMatrix(element),  // 0,0 is the top left corner, but you can use any local coordinates.  localPoint = { x: 0, y: 0 },  // get a new point with the matrix transformations applied.  globalPoint = matrix.apply(localPoint);gsap.to("#dot", {  x: globalPoint.x,  y: globalPoint.y,  ease: "power1.inOut",});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
