# RoughEase | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Eases/RoughEase](https://gsap.com/docs/v3/Eases/RoughEase)  
**Last Updated:** 2025-05-23T00:14:13.729Z  
**Extracted:** 2025-05-31 16:56:03

---

# RoughEase | GSAP | Docs & Learning

Most easing equations give a smooth, gradual transition between the start and end values, but `RoughEase` provides an easy way to get a rough, jagged effect instead, or you can also get an evenly-spaced back-and-forth movement if you prefer. `RoughEase` is in the EasePack file. Configure the `RoughEase` with any of these optional properties:

```
//use the default valuesgsap.from(element, {duration: 1, opacity: 0, ease: "rough"});//or customize the configurationgsap.to(element, {duration: 2, y: 300, ease: "rough({strength: 3, points: 50, template: strong.inOut, taper: both, randomize: false})" });
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
