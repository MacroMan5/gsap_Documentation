# iteration | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Tween/iteration()](https://gsap.com/docs/v3/GSAP/Tween/iteration())  
**Last Updated:** 2025-05-23T00:24:31.109Z  
**Extracted:** 2025-05-31 16:56:03

---

# iteration | GSAP | Docs & Learning

Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.

Gets or sets the iteration (on a repeated tween). For example, iteration is `1` the very first time through, then on the first repeat, the iteration would be `2`, then `3`, etc.

Setting the iteration will cause the tween to go to the iteration provided. For example, if the `repeat` is 4, and the playhead is currently on its third repeat, `.iteration(2)` will make the tween jump back to the second iteration.

```
//gets current iterationvar progress = myTween.iteration();//sets iteration the second iterationmyTween.iteration(2);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
