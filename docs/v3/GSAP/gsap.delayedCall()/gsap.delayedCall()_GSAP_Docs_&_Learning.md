# gsap.delayedCall() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.delayedCall()](https://gsap.com/docs/v3/GSAP/gsap.delayedCall())  
**Last Updated:** 2025-05-23T00:21:32.528Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.delayedCall() | GSAP | Docs & Learning

Provides a simple way to call a function after a set amount of time, completely in-sync with the whole rendering loop (unlike a `setTimeout()` which may fire outside of the browser's screen refresh cycle). You can optionally pass any number of parameters to the function too.

```
//calls myFunction() after 1 second and passes 2 parameters:gsap.delayedCall(1, myFunction, ["param1", "param2"]);function myFunction(param1, param2) {  //do stuff}
```

To cancel/kill a delayed call, save a reference to it and then call .kill() on it when needed:

Or if you don't want to keep a reference to it, you can use the [gsap.killTweensOf()](https://gsap.com/docs/v3/GSAP/gsap.killTweensOf\(\)) method because a delayedCall() is merely a [Tween](https://gsap.com/docs/v3/GSAP/Tween) with an onComplete and the function itself is the "target" of the Tween:

---

*This documentation was extracted from the database for URLs containing 'gsap'*
