# static-getLength | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/DrawSVGPlugin/static.getLength()](https://gsap.com/docs/v3/Plugins/DrawSVGPlugin/static.getLength())  
**Last Updated:** 2025-05-23T00:30:24.210Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-getLength | GSAP | Docs & Learning

## DrawSVGPlugin.getLength

### DrawSVGPlugin.getLength( element:\[Element | Selector text\] ) : Number

Provides an easy way to get the length of an SVG element's stroke including: `<path>`, `<rect>`, `<circle>`, `<ellipse>`, `<line>`, `<polyline>`, and `<polygon>`

#### Parameters

*   #### **element**: \[Element | Selector text\]
    
    The element (or the selector text for the element) whose stroke length you'd like to determine.
    

The length of an SVG element's stroke.

Provides an easy way to get the length of an SVG element's stroke including: `<path>`, `<rect>`, `<circle>`, `<ellipse>`, `<line>`, `<polyline>`, and `<polygon>`.

When combined with the position (obtained using `DrawSVGPlugin.getPosition`), you can calculate the total percentage at any given moment like so:

```
function getPercentage(element) {  return Math.floor(    DrawSVGPlugin.getPosition(element)[1] /      (DrawSVGPlugin.getLength(element) / 100)  );}
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
