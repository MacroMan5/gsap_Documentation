# addEventListener | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/addEventListener()](https://gsap.com/docs/v3/Plugins/Draggable/addEventListener())  
**Last Updated:** 2025-05-23T00:28:30.310Z  
**Extracted:** 2025-05-31 16:56:03

---

# addEventListener | GSAP | Docs & Learning

Registers a function that should be called each time a particular type of event occurs. Inside the listener function `this` refers to the target of the Draggable instance that fired the event.

```
var myDraggable = Draggable.create("#box1", {  bounds: "#container"})[0];myDraggable.addEventListener("press", onPress);function onPress() {  console.log("myDraggable was pressed");  gsap.to(this, {duration: 0.2, backgroundColor: "red"}); // animate the backgroundColor of the target of the Draggable that was pressed}
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
