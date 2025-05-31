# kill | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/kill()](https://gsap.com/docs/v3/GSAP/Timeline/kill())  
**Last Updated:** 2025-05-23T00:27:00.625Z  
**Extracted:** 2025-05-31 16:56:03

---

# kill | GSAP | Docs & Learning

Immediately stops the animation, removing it from its parent timeline, and releasing it for garbage collection. **Note**: don't kill() an animation if you want to use it again later - you could pause() it instead if you want to reuse it.

```
// kill the timelinetl.kill();// set to null so the reference is removedtl = null;
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
