# delay | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/delay()](https://gsap.com/docs/v3/GSAP/Timeline/delay())  
**Last Updated:** 2025-05-23T00:26:00.937Z  
**Extracted:** 2025-05-31 16:56:03

---

# delay | GSAP | Docs & Learning

Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.

Gets or sets the animation's initial `delay` which is the length of time in seconds before the animation should begin. A tween's starting values are not recorded until after the `delay` has expired (except in `from()` tweens which render immediately by default unless `immediateRender: false` is set in the `vars` parameter). An animation's delay is unaffected by its `timeScale`, so if you were to change `timeScale` from 1 to 10, for example, it wouldn't cause the delay to grow tenfold.

This method serves as both a getter and setter. Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining, like `myAnimation.delay(2).timeScale(0.5).play(1);`

```
//gets current delayvar currentDelay = myAnimation.delay();//sets delaymyAnimation.delay(2);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
