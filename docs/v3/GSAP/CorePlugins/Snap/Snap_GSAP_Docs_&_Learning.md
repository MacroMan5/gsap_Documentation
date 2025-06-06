# Snap | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/CorePlugins/Snap](https://gsap.com/docs/v3/GSAP/CorePlugins/Snap)  
**Last Updated:** 2025-05-23T00:15:04.742Z  
**Extracted:** 2025-05-31 16:56:03

---

# Snap | GSAP | Docs & Learning

What are internal plugins?

SnapPlugin is an internal plugin, It is **automatically included in GSAP's core** and **doesn't have to be loaded using gsap.registerPlugin()**.

You can think of internal plugins as just a part of GSAP.

The SnapPlugin allows tweens to "snap" to the closest value in a given array or increment. It basically adds a modifier to any property that implements one of the following snapping behaviors to every value DURING the tween (live, not just to the end value).

```
// snap all of the properties in the comma-delimited list ("x,y" in this case) to the closest whole number:gsap.to(".class", {  x: 1000,  y: 250,  snap: "x,y",});// snap to an increment:gsap.to(".class", {  x: 1000,  snap: {    x: 20, // x snaps to the closest increment of 20 (0, 20, 40, 60, etc.)  },});// snap to the closest value in an array:gsap.to(".class", {  x: 1000,  snap: {    x: [0, 50, 150, 500], // x snaps to the closest value in this array  },});// snap to a value in an array, but only when it's within a certain distance/radius of one of those values:gsap.to(".class", {  x: 1000,  snap: {    x: { values: [0, 50, 150, 500], radius: 20 }, // x snaps to the closest value in the array but only when it's within 20 pixels of it.  },});
```

You can define as many snap properties as you want.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
