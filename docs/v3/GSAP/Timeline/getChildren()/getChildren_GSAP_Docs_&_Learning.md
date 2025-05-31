# getChildren | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/getChildren()](https://gsap.com/docs/v3/GSAP/Timeline/getChildren())  
**Last Updated:** 2025-05-23T00:26:30.023Z  
**Extracted:** 2025-05-31 16:56:03

---

# getChildren | GSAP | Docs & Learning

An Array of child tweens and timelines.

Returns an array containing all the tweens and/or timelines nested in this timeline that match the provided criteria. Callbacks (delayed calls) are considered zero-duration tweens.

```
//first, let's set up a master timeline and nested timeline:var master = gsap.timeline({ defaults: { duration: 1 } }),  nested = gsap.timeline();//drop 2 tweens into the nested timelinenested.to("#e1", { duration: 1, x: 100 }).to("#e2", { duration: 2, y: 200 });//drop 3 tweens into the master timelinemaster  .to("#e3", { top: 200 })  .to("#e4", { left: 100 })  .to("#e5", { backgroundColor: "red" });//nest the timeline:master.add(nested);//get only the direct children of the master timeline:var children = master.getChildren(false, true, true);console.log(children.length); //"3" (2 tweens and 1 timeline)//get all of the tweens/timelines (including nested ones) that occur AFTER 0.5 secondschildren = master.getChildren(true, true, true, 0.5);console.log(children.length); //"5" (4 tweens and 1 timeline)//get only tweens (not timelines) of master (including nested tweens):children = master.getChildren(true, true, false);console.log(children.length); //"5" (5 tweens)
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
