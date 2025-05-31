# smoothOriginChange | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/smoothOriginChange](https://gsap.com/docs/v3/HelperFunctions/helpers/smoothOriginChange)  
**Last Updated:** 2025-05-23T00:20:45.729Z  
**Extracted:** 2025-05-31 16:56:03

---

# smoothOriginChange | GSAP | Docs & Learning

If you want to change `transformOrigin` dynamically without a jump, you'd need to compensate its translation (x/y). Here's a function I whipped together for that purpose:

```
function smoothOriginChange(targets, transformOrigin) {  gsap.utils.toArray(targets).forEach(function (target) {    var before = target.getBoundingClientRect();    gsap.set(target, { transformOrigin: transformOrigin });    var after = target.getBoundingClientRect();    gsap.set(target, {      x: "+=" + (before.left - after.left),      y: "+=" + (before.top - after.top),    });  });}
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
