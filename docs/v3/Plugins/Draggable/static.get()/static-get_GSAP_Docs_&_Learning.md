# static-get | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/static.get()](https://gsap.com/docs/v3/Plugins/Draggable/static.get())  
**Last Updated:** 2025-05-23T00:28:52.612Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-get | GSAP | Docs & Learning

The Draggable instance that's associated with the target element (or `undefined` if none exists).

Provides an easy way to get the Draggable instance that's associated with a particular DOM element. For example, maybe you made all of the elements with the class "draggable" draggable by calling `Draggable.create(".draggable")` and then you want to find the individual Draggable instance that's associated with the element with an ID of "element1" that'd be as simple as:

```
var draggable = Draggable.get("#element1"); //or use the element itself instead of a selector string: var myElement =
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
