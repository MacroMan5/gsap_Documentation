# static-snapDirectional | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.snapDirectional()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.snapDirectional())  
**Last Updated:** 2025-05-23T00:33:49.853Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-snapDirectional | GSAP | Docs & Learning

A function that accepts two parameters - 1) a value to snap, 2) the direction where 1 is forward (greater than) and -1 is backward (less than)

Returns a snapping function to which you can feed any value to snap, along with a direction where `1` is forward (greater than) and `-1` is backward (less than). For example:

```
// returns a function that snaps to the closest increment of 5let snap = ScrollTrigger.snapDirectional(5);snap(11); // 10 (closest, not directional)snap(11, 1); // 15 (closest greater than)snap(11, -1); // 10 (closest less than)
```

```
let values = [0, 5, 20, 100];// returns a function that'll snap to the closest value in the Arraylet snap = ScrollTrigger.snapDirectional(values);snap(8); // 5  (closest, non-directional)snap(8, 1); // 20 (closest greater than)snap(99, -1); // 20 (closest less than)
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
