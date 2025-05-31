# unitize | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/UtilityMethods/unitize()](https://gsap.com/docs/v3/GSAP/UtilityMethods/unitize())  
**Last Updated:** 2025-05-23T00:13:54.036Z  
**Extracted:** 2025-05-31 16:56:03

---

# unitize | GSAP | Docs & Learning

Think of `unitize()` like a wrapper around **another** function, ensuring that the result gets a unit applied, like `"px"` or `"%"`. For example, perhaps you have a function that only deals with raw numbers like [wrap()](https://gsap.com/docs/v3/GSAP/UtilityMethods/wrap\(\)), but you need the result to get a `"px"` added to the end. Or maybe the incoming values have units so you need those removed before being fed into your function ([wrap()](https://gsap.com/docs/v3/GSAP/UtilityMethods/wrap\(\)) in this example), and then that same unit put back onto the end of the result. No problem!

```
// get a function that always applies "px" to the result (and strips off any units from the input)var clamp = gsap.utils.unitize(gsap.utils.clamp(0, 100), "px");// now the result always gets "px" added:clamp(132); // "100px"clamp("-20%"); // "0px" (notice the unit change)clamp(50); // "50px"// or use whatever unit is in the input:var wrap = gsap.utils.unitize(gsap.utils.wrap(0, 100)); // no specific unit is declared in unitize()wrap("150px"); // 50pxwrap("130%"); // 30%// another example of forcing a unit like "%":var map = gsap.utils.unitize(gsap.utils.mapRange(-10, 10, 0, 100), "%");map(0); // 50%map("5px"); // 75%// useful in modifier functions:gsap.to(".class", {  x: 1000,  modifiers: {    //the value fed into this function will have unit - this strips it off to feed in a raw number to wrap() and then slaps "px" onto the result.    x: gsap.utils.unitize(gsap.utils.wrap(0, window.innerWidth), "px"),  },});
```

Note: `unitize()` strips off any units from the input (using `parseFloat()`) before passing it along to the `function`.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
