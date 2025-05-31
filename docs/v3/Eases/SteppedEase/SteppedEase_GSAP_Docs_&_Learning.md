# SteppedEase | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Eases/SteppedEase](https://gsap.com/docs/v3/Eases/SteppedEase)  
**Last Updated:** 2025-05-23T00:14:58.619Z  
**Extracted:** 2025-05-31 16:56:03

---

# SteppedEase | GSAP | Docs & Learning

Most easing equations give a smooth, gradual transition between the start and end values, but SteppedEase provides an easy way to define a specific number of steps that the transition should take.

For example, if x is 0 and you want to tween it to 100 with 5 steps (20, 40, 60, 80, and 100) over the course of 2 seconds, you'd do:

```
gsap.to(obj, {duration: 2, x: 100, ease: "steps(5)"});
```

**Note:** SteppedEase is optimized for use with the GreenSock Animation Platform, so it isn't intended to be used with other engines. Specifically, its easing equation always returns values between 0 and 1.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
