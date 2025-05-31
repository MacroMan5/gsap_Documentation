# getNestedLabelTime | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/getNestedLabelTime](https://gsap.com/docs/v3/HelperFunctions/helpers/getNestedLabelTime)  
**Last Updated:** 2025-05-23T00:20:20.662Z  
**Extracted:** 2025-05-31 16:56:03

---

# getNestedLabelTime | GSAP | Docs & Learning

Labels are timeline-specific, so you can't tell a timeline to move its playhead to a label that exists in a **nested** timeline. So here's a helper function that lets you find a nested label and calculate where that lines up on the \[parent/ancestor\] timeline:

```
function getNestedLabelTime(timeline, label) {  let children = timeline.getChildren(true, false, true),    i = children.length,    tl,    time;  while (i--) {    if (label in children[i].labels) {      tl = children[i];      time = tl.labels[label];      break;    }  }  if (tl) {    while (tl !== timeline) {      time = tl.startTime() + time / tl.timeScale();      tl = tl.parent;    }  }  return time;}
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
