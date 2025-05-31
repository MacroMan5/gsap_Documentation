# duration | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Tween/duration()](https://gsap.com/docs/v3/GSAP/Tween/duration())  
**Last Updated:** 2025-05-23T00:23:46.922Z  
**Extracted:** 2025-05-31 16:56:03

---

# duration | GSAP | Docs & Learning

Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.

Gets or sets the animation's `duration`, not including any `repeat`s or `repeatDelay`s. For example, if a tween has a `duration` of 2 and a `repeat` of 3, its `totalDuration` would be 8 (one standard play plus 3 repeats equals 4 total cycles).

This method serves as both a getter and setter. Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining, like `myAnimation.duration(2).delay(0.5).play(1);`

```
var currentDuration = myAnimation.duration(); //gets current durationmyAnimation.duration(2); //sets duration
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
