# totalDuration | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Tween/totalDuration()](https://gsap.com/docs/v3/GSAP/Tween/totalDuration())  
**Last Updated:** 2025-05-23T00:24:54.546Z  
**Extracted:** 2025-05-31 16:56:03

---

# totalDuration | GSAP | Docs & Learning

Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.

Gets or sets the total duration of the tween in seconds including any repeats or repeatDelays. `duration`, by contrast, does **NOT** include repeats and repeatDelays. For example, if the tween has a `duration` of 10, a `repeat` of 1 and a `repeatDelay` of 2, the `totalDuration` would be 22.

This method serves as both a getter and setter. Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.

```
//gets total durationvar total = myTween.totalDuration();//sets the total durationmyTween.totalDuration(10);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
