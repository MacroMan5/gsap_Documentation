# static-convertToPath | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.convertToPath()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.convertToPath())  
**Last Updated:** 2025-05-23T00:31:15.039Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-convertToPath | GSAP | Docs & Learning

## MotionPathPlugin.convertToPath

### MotionPathPlugin.convertToPath( shape:String | Element, swap:Boolean ) : Array

Converts SVG shapes like `<circle>`, `<rect>`, `<ellipse>`, or `<line>` into `<path>`

#### Parameters

*   #### **shape**: String | Element
    
    Selector text or Element reference that should be converted
    
*   #### **swap**: Boolean
    
    By default, the resulting <path> will be swapped directly into the DOM in place of the provided shape element, but you can define `false` for `swap` to prevent that.
    

### Returns : Array[​](#returns--array "Direct link to Returns : Array")

An Array of the resulting `<path>` elements

### Details[​](#details "Direct link to Details")

Identical to the [`MorphSVGPlugin.convertToPath()`](https://gsap.com/docs/v3/Plugins/MorphSVGPlugin/static.convertToPath) method. Please see the corresponding MorphSVG [documentation for that method](https://gsap.com/docs/v3/Plugins/MorphSVGPlugin/static.convertToPath) (includes a video).

---

*This documentation was extracted from the database for URLs containing 'gsap'*
