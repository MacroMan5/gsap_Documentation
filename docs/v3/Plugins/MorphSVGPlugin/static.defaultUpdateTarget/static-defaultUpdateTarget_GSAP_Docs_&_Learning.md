# static-defaultUpdateTarget | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/MorphSVGPlugin/static.defaultUpdateTarget](https://gsap.com/docs/v3/Plugins/MorphSVGPlugin/static.defaultUpdateTarget)  
**Last Updated:** 2025-05-23T00:30:57.238Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-defaultUpdateTarget | GSAP | Docs & Learning

## MorphSVGPlugin.defaultUpdateTarget

### MorphSVGPlugin.defaultUpdateTarget : Boolean

Sets the default `updateTarget` value for all MorphSVG animations; if `true`, the original tween target (typically an SVG `<path>` element) itself gets updated during the tween.

### Details[​](#details "Direct link to Details")

Sets the default `updateTarget` value for all MorphSVG animations; if `true`, the original tween target (typically an SVG `<path>` element) itself gets updated during the tween. If you've got a render function set up to draw to `<canvas>`, for example, then it may be wasteful to update the original target as well (duplicate efforts). Ultimately this is a performance optimization. Setting it to `false` allows MorphSVG to skip that step.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
