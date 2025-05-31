# paused | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollSmoother/paused()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/paused())  
**Last Updated:** 2025-05-23T00:27:56.537Z  
**Extracted:** 2025-05-31 16:56:03

---

# paused | GSAP | Docs & Learning

Gets/Sets the paused state - if `true`, nothing will scroll (except via [scrollTop()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/scrollTop\(\)) or [scrollTo()](https://gsap.com/docs/v3/Plugins/ScrollSmoother/scrollTo\(\)) on this instance).

Pausing immediately stops movement and prevents the user from even moving the scrollbar.

```
document.querySelector("#toggle").addEventListener("click", () => {  // toggle!  smoother.paused(!smoother.paused());});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
