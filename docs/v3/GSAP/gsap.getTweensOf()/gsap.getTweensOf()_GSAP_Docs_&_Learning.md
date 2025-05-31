# gsap.getTweensOf() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.getTweensOf()](https://gsap.com/docs/v3/GSAP/gsap.getTweensOf())  
**Last Updated:** 2025-05-23T00:22:01.816Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.getTweensOf() | GSAP | Docs & Learning

Returns an array containing all the tweens of a particular target (or group of targets) that have not yet been released for garbage collection.

Returns an array containing all the tweens of a particular target (or group of targets) that have not yet been released for garbage collection which typically happens when the tween completes. For example, `gsap.getTweensOf(".myClass")` returns an array of all tweens of elements with the "myClass" class applied. You can pass in the actual element/target/object instead, of course.

Since the method only finds tweens that haven't been released for garbage collection, if you create a tween and then let it finish and then a while later try to find it with `getTweensOf()`, it may not be found because it was released by the engine for garbage collection. Remember, one of the best parts of GSAP is that it saves you from the headache of managing garbage collection chores. Otherwise, you'd need to manually dispose each tween you create, making things much more cumbersome.

```
gsap.to(obj1, { x: 100 });gsap.to(obj2, { x: 100 });gsap.to([obj1, obj2], { opacity: 0 });var a1 = gsap.getTweensOf(obj1); //finds 2 tweensvar a2 = gsap.getTweensOf([obj1, obj2]); //finds 3 tweens
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
