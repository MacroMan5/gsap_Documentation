# applyBounds | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/applyBounds()](https://gsap.com/docs/v3/Plugins/Draggable/applyBounds())  
**Last Updated:** 2025-05-23T00:28:31.419Z  
**Extracted:** 2025-05-31 16:56:03

---

# applyBounds | GSAP | Docs & Learning

### applyBounds( bounds:Element | String | Object ) ;

Applies new bounds to the Draggable.

#### Parameters

*   #### **bounds**: Element | String | Object
    
    The bounds to restrict the Draggable to. It could be an element reference, selector text, or an object with the values {top: 100, left: 0, width: 1000, height: 800} or {minX: 10, maxX: 300, minY: 50, maxY: 500} or {minRotation: 0, maxRotation: 270}.
    

### Details[​](#details "Direct link to Details")

Applies new bounds to the Draggable.

The bounds could be another another DOM element (like a container) using an element reference (like document.getElementById("container")) or selector text (like `"#container"`), rectangle coordinates (like `{top: 100, left: 0, width: 1000, height: 800}` which is based on the parent's coordinate system where top and left would be from the upper left corner of the parent), or specific maximum and minimum values like `{minX: 10, maxX: 300, minY: 50, maxY: 500}` or `{minRotation: 0, maxRotation: 270}`.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
