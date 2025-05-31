# seek | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Tween/seek()](https://gsap.com/docs/v3/GSAP/Tween/seek())  
**Last Updated:** 2025-05-23T00:23:46.530Z  
**Extracted:** 2025-05-31 16:56:03

---

# seek | GSAP | Docs & Learning

Jumps to a specific time without affecting whether or not the instance is paused or reversed.

If there are any events/callbacks inbetween where the playhead was and the new time, they will not be triggered because by default `suppressEvents` (the 2nd parameter) is `true`. Think of it like picking the needle up on a record player and moving it to a new position before placing it back on the record. If, however, you do not want the events/callbacks suppressed during that initial move, simply set the `suppressEvents` parameter to `false`.

```
//jumps to exactly 2 secondsmyAnimation.seek(2);//jumps to exactly 2 seconds but doesn't suppress events during the initial move:myAnimation.seek(2, false);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
