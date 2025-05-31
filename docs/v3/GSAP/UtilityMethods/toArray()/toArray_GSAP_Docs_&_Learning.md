# toArray | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/UtilityMethods/toArray()](https://gsap.com/docs/v3/GSAP/UtilityMethods/toArray())  
**Last Updated:** 2025-05-23T00:13:53.720Z  
**Extracted:** 2025-05-31 16:56:03

---

# toArray | GSAP | Docs & Learning

Converts selector text, an Array of objects or selector text, a NodeList, an object, or almost any Array-like object into a flat `Array`. You can optionally define a scope (added in 3.7.0) for the selector text which limits results to descendants of that scope Element.

```
// these all return the corresponding elements wrapped in a flat Array:// selector text (returns the raw elements wrapped in an Array)let targets = gsap.utils.toArray(".class");// raw element/objectlet targets = gsap.utils.toArray(myElement);// Array of selector text (same result as ".class1, .class2")let targets = gsap.utils.toArray([".class1", ".class2"]);// Only descendant elements of myElementlet targets = gsap.utils.toArray(".class", myElement);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
