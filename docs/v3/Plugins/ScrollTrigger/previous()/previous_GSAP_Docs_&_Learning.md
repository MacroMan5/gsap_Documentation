# previous | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/previous()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/previous())  
**Last Updated:** 2025-05-23T00:34:21.707Z  
**Extracted:** 2025-05-31 16:56:03

---

# previous | GSAP | Docs & Learning

Returns the previous ScrollTrigger in the refresh order. This can be useful in advanced scenarios where you want to base one ScrollTrigger's start/end value on the previous one's:

```
ScrollTrigger.create({  start: self => self.previous().end, // start at the end of the previous ScrollTrigger  ...});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
