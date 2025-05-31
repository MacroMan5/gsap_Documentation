# repeatDelay | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/repeatDelay()](https://gsap.com/docs/v3/GSAP/Timeline/repeatDelay())  
**Last Updated:** 2025-05-23T00:26:17.747Z  
**Extracted:** 2025-05-31 16:56:03

---

# repeatDelay | GSAP | Docs & Learning

Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.

Gets or sets the number of times that the timeline should repeat after its first iteration.

For example, if `repeat` is 2 and `repeatDelay` is 1, the timeline will play initially, then wait for 1 second before it repeats, then play again, then wait 1 second again before doing its final repeat. You can set the initial `repeatDelay` value via the `vars` parameter, like:

```
var tl = gsap.timeline({ repeat: 2, repeatDelay: 1 });
```

This method serves as both a getter and setter. Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining, like `myTimeline.repeat(2).yoyo(true).play();`

---

*This documentation was extracted from the database for URLs containing 'gsap'*
