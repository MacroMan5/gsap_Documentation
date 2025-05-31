# nextLabel | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/nextLabel()](https://gsap.com/docs/v3/GSAP/Timeline/nextLabel())  
**Last Updated:** 2025-05-23T00:25:29.512Z  
**Extracted:** 2025-05-31 16:56:03

---

# nextLabel | GSAP | Docs & Learning

Name of the label that is after the time passed to `nextLabel()`. If no `time` is provided, the timeline's current playhead time will be used.

Returns the next label (if any) that occurs **after** the `time` parameter. If no `time` is provided, the timeline's current playhead time will be used. It makes no difference if the timeline is reversed ("after" means later in the timeline's local time zone).

A label that is positioned exactly at the same `time` as the time parameter will be ignored.

You could use `nextLabel()` in conjunction with `tweenTo()` to make the timeline tween to the next label like this:

```
tl.tweenTo(tl.nextLabel());
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
