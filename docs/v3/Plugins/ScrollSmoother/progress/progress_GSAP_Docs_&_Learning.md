# progress | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollSmoother/progress](https://gsap.com/docs/v3/Plugins/ScrollSmoother/progress)  
**Last Updated:** 2025-05-23T00:27:39.923Z  
**Extracted:** 2025-05-31 16:56:03

---

# progress | GSAP | Docs & Learning

The progress value of the overall page scroll where 0 is at the very top and 1 is at the very bottom and 0.5 is halfway scrolled. This value will animate during the smooth scrolling and end when the `onStop` fires.

```
ScrollSmoother.create({  smooth: 1,  onUpdate: (self) => console.log("progress", self.progress),});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
