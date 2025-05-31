# checkPrefix | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/UtilityMethods/checkPrefix()](https://gsap.com/docs/v3/GSAP/UtilityMethods/checkPrefix())  
**Last Updated:** 2025-05-23T00:15:20.415Z  
**Extracted:** 2025-05-31 16:56:03

---

# checkPrefix | GSAP | Docs & Learning

Give `checkPrefix()` any CSS property name and it will return the appropriate, browser-prefixed version (if necessary) of that property. If no prefix is needed, it will return the original property name. If the property does not exist, it will return `undefined`. For example:

```
//the following may return "filter", "WebkitFilter", or "MozFilter" depending on your browservar filterProperty = gsap.utils.checkPrefix("filter");
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
