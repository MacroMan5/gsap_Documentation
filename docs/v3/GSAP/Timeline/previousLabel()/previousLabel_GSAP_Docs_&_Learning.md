# previousLabel | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/previousLabel()](https://gsap.com/docs/v3/GSAP/Timeline/previousLabel())  
**Last Updated:** 2025-05-23T00:25:40.412Z  
**Extracted:** 2025-05-31 16:56:03

---

# previousLabel | GSAP | Docs & Learning

Name of the label that is before the time passed to `previousLabel()`. If no `time` is provided, the timeline's current playhead time will be used.

Returns the previous label (if any) that occurs **before** the `time` parameter. If no `time` is provided, the timeline's current playhead time will be used. It makes no difference if the timeline is reversed ("before" means earlier in the timeline's local time zone).

A label that is positioned exactly at the same `time` as the time parameter will be ignored.

You could use `previousLabel()` in conjunction with `tweenTo()` to make the timeline tween back to the previous label like this:

```
tl.tweenTo(tl.previousLabel());
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
