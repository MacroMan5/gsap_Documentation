# static-editPath | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/MotionPathHelper/static.editPath()](https://gsap.com/docs/v3/MotionPathHelper/static.editPath())  
**Last Updated:** 2025-05-23T00:31:52.417Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-editPath | GSAP | Docs & Learning

Makes an SVG `<path>` editable in the browser.

```
MotionPathHelper.editPath("#my-path", {  handleSize: 7,  selected: true,  draggable: true,  onPress: () => console.log("pressed"),  onRelease: () => console.log("released"),  onUpdate: () => console.log("updated"),  onDeleteAnchor: () => console.log("deleted anchor"),});
```

You can optionally pass in a `vars` parameter to further configure the path editor. It's an object and can include any of the following properties:

---

*This documentation was extracted from the database for URLs containing 'gsap'*
