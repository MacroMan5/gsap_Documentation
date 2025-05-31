# blendEases | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/blendEases](https://gsap.com/docs/v3/HelperFunctions/helpers/blendEases)  
**Last Updated:** 2025-05-23T00:19:45.236Z  
**Extracted:** 2025-05-31 16:56:03

---

# blendEases | GSAP | Docs & Learning

If you need one ease at the start of your animation, and a different one at the end, you can use this function to blend them!

```
//just feed in the starting ease and the ending ease (and optionally an ease to do &#xFEFF;the blending), and it'll return a new Ease that's...blended!function blendEases(startEase, endEase, blender) {  var parse = function (ease) {      return typeof ease === "function" ? ease : gsap.parseEase("power4.inOut");    },    s = gsap.parseEase(startEase),    e = gsap.parseEase(endEase),    blender = parse(blender);  return function (v) {    var b = blender(v);    return s(v) * (1 - b) + e(v) * b;  };}//example usage:gsap.to("#target", {  duration: 2,  x: 100,  ease: blendEases("back.in(1.2)", "bounce"),});
```

If you need to **invert** an ease instead, see [this demo](https://codepen.io/GreenSock/pen/rgROxY?editors=0010) for a different helper function.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
