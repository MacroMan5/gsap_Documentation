# static-create | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.create()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.create())  
**Last Updated:** 2025-05-23T00:32:54.237Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-create | GSAP | Docs & Learning

Creates a new standalone ScrollTrigger instance. You don't need to put ScrollTriggers directly into animations (though that's probably the most common use case). With a standalone ScrollTrigger, you can tap into the rich callback system to do almost anything.

```
ScrollTrigger.create({  trigger: "#id",  start: "top top",  endTrigger: "#otherID",  end: "bottom 50%+=100px",  onToggle: (self) => console.log("toggled, isActive:", self.isActive),  onUpdate: (self) => {    console.log(      "progress:",      self.progress.toFixed(3),      "direction:",      self.direction,      "velocity",      self.getVelocity()    );  },});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
