# reversed | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/reversed()](https://gsap.com/docs/v3/GSAP/Timeline/reversed())  
**Last Updated:** 2025-05-23T00:26:30.243Z  
**Extracted:** 2025-05-31 16:56:03

---

# reversed | GSAP | Docs & Learning

Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.

Gets or sets the animation's reversed state which indicates whether or not the animation should be played backwards. This value is not affected by `yoyo` repeats and it does not take into account the reversed state of ancestor timelines. So for example, a tween that is not reversed might appear reversed if its parent timeline (or any ancestor timeline) is reversed.

This method serves as both a getter and setter. Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.

```
//gets current orientationvar isReversed = tl.reversed();//sets the orientation to reversedtl.reversed(true);//toggles the orientationtl.reversed(!tl.reversed());
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
