# gsap.defaults() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.defaults()](https://gsap.com/docs/v3/GSAP/gsap.defaults())  
**Last Updated:** 2025-05-23T00:21:31.449Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.defaults() | GSAP | Docs & Learning

`gsap.defaults()` lets you set properties that should be inherited by **ALL** tweens (that don't have `inherit:false` set) unless overridden by that tween. General configuration settings that aren't Tween-specific (like `units`, `autoSleep`, and `force3D`) should be set using [`gsap.config()`](https://gsap.com/docs/v3/GSAP/gsap.config\(\)) instead.

For example, if you want to change the default `ease` and `duration` of all tweens you'd do:

```
gsap.defaults({  ease: "power2.in",  duration: 1,});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
