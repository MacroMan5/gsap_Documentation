# EndArray | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/CorePlugins/EndArray](https://gsap.com/docs/v3/GSAP/CorePlugins/EndArray)  
**Last Updated:** 2025-05-23T00:14:57.612Z  
**Extracted:** 2025-05-31 16:56:03

---

# EndArray | GSAP | Docs & Learning

What are internal plugins?

EndArrayPlugin is an internal plugin, It is **automatically included in GSAP's core** and **doesn't have to be loaded using gsap.registerPlugin()**.

You can think of internal plugins as just a part of GSAP.

The endArray plugin enables you to tween an Array of numeric values to a different Array of numeric values with easing applied.

```
const arr = [1, 2, 3];gsap.to(arr, {  endArray: [5, 6, 7],  onUpdate() {    console.log(arr);  },});
```

If you have Arrays of uneven lengths, only the indexes that are in both Arrays will be animated.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
