# killChildTweensOf | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/killChildTweensOf](https://gsap.com/docs/v3/HelperFunctions/helpers/killChildTweensOf)  
**Last Updated:** 2025-05-23T00:20:31.419Z  
**Extracted:** 2025-05-31 16:56:03

---

# killChildTweensOf | GSAP | Docs & Learning

You can kill all tweening elements that are children of a given target by using this function:

```
function killChildTweensOf(ancestor) {  ancestor = gsap.utils.toArray(ancestor)[0];  gsap.globalTimeline    .getChildren(true, true, false)    .forEach((tween) =>      tween        .targets()        .forEach((e) => e.nodeType && ancestor.contains(e) && tween.kill(e))    );}
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
