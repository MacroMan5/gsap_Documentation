# callAfterResize | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/callAfterResize](https://gsap.com/docs/v3/HelperFunctions/helpers/callAfterResize)  
**Last Updated:** 2025-05-23T00:19:53.812Z  
**Extracted:** 2025-05-31 16:56:03

---

# callAfterResize | GSAP | Docs & Learning

"resize" events get dispatched **many** times while the user is dragging the browser window's edges, so if you run an expensive function on every resize event, it can really bog things down. Here's a function that will wait to call your function until a certain amount of time has elapsed since the user STOPPED resizing the window (by default, it's 0.2 seconds):

```
function callAfterResize(func, delay) {  let dc = gsap.delayedCall(delay || 0.2, func).pause(),    handler = () => dc.restart(true);  window.addEventListener("resize", handler);  return handler; // in case you want to window.removeEventListener() later}
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
