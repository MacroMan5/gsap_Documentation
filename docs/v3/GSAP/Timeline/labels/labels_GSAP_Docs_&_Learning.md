# labels | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/labels](https://gsap.com/docs/v3/GSAP/Timeline/labels)  
**Last Updated:** 2025-05-23T00:25:13.032Z  
**Extracted:** 2025-05-31 16:56:03

---

# labels | GSAP | Docs & Learning

This stores any labels that have been added to the timeline. You can get the full object with all labels by using `timeline.labels`. For example:

```
var tl = gsap.timeline();tl.addLabel("myLabel", 3);tl.addLabel("anotherLabel", 5);//now the label object has those labels and times, like:console.log(tl.labels.myLabel); // 3console.log(tl.labels.anotherLabel); // 5
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
