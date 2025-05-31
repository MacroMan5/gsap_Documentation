# gsap.set() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.set()](https://gsap.com/docs/v3/GSAP/gsap.set())  
**Last Updated:** 2025-05-23T00:22:33.828Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.set() | GSAP | Docs & Learning

Immediately sets properties of the target(s) accordingly - essentially a zero-duration [to()](https://gsap.com/docs/v3/GSAP/gsap.to\(\)) tween with a more intuitive name. So the following lines produce identical results:

```
gsap.set(".class", { x: 100, y: 50, opacity: 0 });gsap.to(".class", { duration: 0, x: 100, y: 50, opacity: 0 });
```

And of course you can use an array or selector text to set the properties of multiple targets at the same time, like:

```
gsap.set([obj1, obj2, obj3], { x: 100, y: 50, opacity: 0 });
```

If you find yourself setting the same property of the same object over and over again many times (like in a pointermove event), consider using [gsap.quickSetter()](https://gsap.com/docs/v3/GSAP/gsap.quickSetter\(\)) because it can deliver even better performance.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
