# animation | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/animation](https://gsap.com/docs/v3/Plugins/ScrollTrigger/animation)  
**Last Updated:** 2025-05-23T00:33:09.735Z  
**Extracted:** 2025-05-31 16:56:03

---

# animation | GSAP | Docs & Learning

\[read-only\] The [Tween](https://gsap.com/docs/v3/GSAP/Tween) or [Timeline](https://gsap.com/docs/v3/GSAP/Timeline) associated with the ScrollTrigger instance (if any). ScrollTriggers don't have to have any animation associated with them, of course, in which case `animation` will be undefined.

```
let tween = gsap.to(".class", {  x: 100,  id: "example",  scrollTrigger: ".trigger",});console.log(ScrollTrigger.getById("example").animation); // tween
```

```
let tween = gsap.to(".class", { x: 100 }),  st = ScrollTrigger.create({    trigger: ".trigger",    start: "top center",    end: "+=500",    animation: tween,  });console.log(st.animation); // tween
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
