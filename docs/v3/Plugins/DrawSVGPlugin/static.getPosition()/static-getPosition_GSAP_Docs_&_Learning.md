# static-getPosition | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/DrawSVGPlugin/static.getPosition()](https://gsap.com/docs/v3/Plugins/DrawSVGPlugin/static.getPosition())  
**Last Updated:** 2025-05-23T00:30:30.814Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-getPosition | GSAP | Docs & Learning

The position of an SVG element's stroke.

Provides an easy way to get the position of an SVG element's stroke including: `<path>`, `<rect>`, `<circle>`, `<ellipse>`, `<line>`, `<polyline>`, and `<polygon>`.

When combined with the length (obtained using `DrawSVGPlugin.getLength`), you can calculate the total percentage at any given moment like so:

```
function getPercentage(element) {  return Math.floor(    DrawSVGPlugin.getPosition(element)[1] /      (DrawSVGPlugin.getLength(element) / 100)  );}
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
