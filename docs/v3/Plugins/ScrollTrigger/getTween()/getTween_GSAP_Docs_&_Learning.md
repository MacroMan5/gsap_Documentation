# getTween | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/getTween()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/getTween())  
**Last Updated:** 2025-05-23T00:34:08.627Z  
**Extracted:** 2025-05-31 16:56:03

---

# getTween | GSAP | Docs & Learning

Returns the `**scrub**` tween (default) which is what gradually makes the animation catch up with the scrollbar position. Or if you call `getTween(true)`, the `**snap**` Tween will be returned instead (if there's a snap in-progress). This allows you to, for example, force the `scrub` or `snap` to its end or kill it, like:

```
let st = ScrollTrigger.create({  animation: myTween,  scrub: 1,  trigger: ".panel-1",});// then later...st.getTween().progress(1); // force the scrub to its end to make it catch up with the current scroll position immediately
```

Or to interrupt a snap...

```
let anim = gsap.to(panels, {  x: () => (panels.length - 1) * window.innerWidth,  scrollTrigger: {    trigger: ".container",    snap: 1 / (panels.length - 1),    pin: true,    end: "+=3000",  },});// then later...let snap = anim.scrollTrigger.getTween(true);if (snap) {  snap.progress(1).kill(); // force the snap to its end and kill it}
```

Obviously this is only helpful if a `scrub` or `snap` value is defined when you set up your ScrollTrigger.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
