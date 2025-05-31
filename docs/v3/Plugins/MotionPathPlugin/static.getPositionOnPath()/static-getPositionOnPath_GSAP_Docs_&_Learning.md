# static-getPositionOnPath | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getPositionOnPath()](https://gsap.com/docs/v3/Plugins/MotionPathPlugin/static.getPositionOnPath())  
**Last Updated:** 2025-05-23T00:31:28.113Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-getPositionOnPath | GSAP | Docs & Learning

An object containing `x` and `y` properties (coordinates) and if the `includeAngle` parameter was `true`, an `angle` property as well (in degrees)

Calculates the x/y position (and optionally the angle) corresponding to a particular progress value (0-1 where 0.5 is the middle) along the RawPath. Note that the RawPath must have had its measurements cached FIRST, using the cacheRawPathMeasurements() method.

```
// Get the RawPath associated with the`<path>`with an ID of "path"let rawPath = MotionPathPlugin.getRawPath("#path"),    point;// cache the measurements first (only necessary once, unless the path data changes)MotionPathPlugin.cacheRawPathMeasurements(rawPath);// find the coordinates and angle of the middle of the pathpoint = MotionPathPlugin.getPositionOnPath(rawPath, 0.5, true);// move a #dot element there...gsap.to("#dot", {    x: point.x,    y: point.y,    rotation: point.angle});```
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
