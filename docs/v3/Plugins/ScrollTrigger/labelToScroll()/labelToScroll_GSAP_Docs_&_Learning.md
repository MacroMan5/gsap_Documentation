# labelToScroll | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/labelToScroll()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/labelToScroll())  
**Last Updated:** 2025-05-23T00:34:19.121Z  
**Extracted:** 2025-05-31 16:56:03

---

# labelToScroll | GSAP | Docs & Learning

Converts a timeline label into the associated scroll position (only applicable to ScrollTriggers whose "animation" is a timeline). This can be quite convenient if, for example, you want to allow users to scroll directly to a position on the page associated with that timeline label.

```
btn.addEventListener("click", () => {  gsap.to(window, { scrollTo: tl.scrollTrigger.labelToScroll("myLabel") });});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
