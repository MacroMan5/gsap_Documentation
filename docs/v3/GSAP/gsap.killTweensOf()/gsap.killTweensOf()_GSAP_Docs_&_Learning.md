# gsap.killTweensOf() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.killTweensOf()](https://gsap.com/docs/v3/GSAP/gsap.killTweensOf())  
**Last Updated:** 2025-05-23T00:22:08.326Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.killTweensOf() | GSAP | Docs & Learning

Kills all the tweens (or specific tweening properties) of a particular object or the delayedCalls to a particular function. If, for example, you want to kill all tweens of elements with the class `"myClass"`, you'd do this:

```
gsap.killTweensOf(".myClass");
```

To kill only particular tweening properties of the object, use the second parameter. For example, if you only want to kill all the tweens of `myObject.opacity` and `myObject.x`, you'd do this:

```
gsap.killTweensOf(myObject, "opacity,x");
```

To kill all the delayedCalls (like ones created using `gsap.delayedCall(5, myFunction);`), you can simply call`gsap.killTweensOf(myFunction);` because delayedCalls are simply tweens that have their `target` and `onComplete` set to the same function (as well as a `delay` of course).

You can also pass in a string that defines selector text, like `"#myID"` to kill the tweens of the element with an ID of "myID" or `"*"` to kill all tweens with DOM targets. You may also pass in an array of targets.

`killTweensOf()` affects tweens that haven't begun yet too. If, for example, a tween of `myObject` has a `delay` of 5 seconds and`gsap.killTweensOf(myObject)` is called 2 seconds after the tween was created, it will still be killed even though it hasn't started yet.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
