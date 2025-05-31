# gsap.registerEase() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.registerEase()](https://gsap.com/docs/v3/GSAP/gsap.registerEase())  
**Last Updated:** 2025-05-23T00:22:27.119Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.registerEase() | GSAP | Docs & Learning

Use `gsap.registerEase()` to register your own easing function with GSAP, giving it a name that can be referenced in any animations. These eases generally return values between 0 and 1 but can go outside of that range (like GSAP's elastic ease).

```
gsap.registerEase("myEaseName", function (progress) {  return progress; //linear});//now we can apply the ease in any tween like:gsap.to(".class", { x: 100, ease: "myEaseName" });
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
