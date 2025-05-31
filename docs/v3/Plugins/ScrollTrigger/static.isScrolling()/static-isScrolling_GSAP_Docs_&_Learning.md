# static-isScrolling | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.isScrolling()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.isScrolling())  
**Last Updated:** 2025-05-23T00:33:08.813Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-isScrolling | GSAP | Docs & Learning

If true, there is a ScrollTrigger-related scroller that's in the process of scrolling

Indicates whether or not any ScrollTrigger-related scroller is in the process of scrolling. Due to the fact that it's impossible to know EXACTLY when scrolling ends ("scroll" events get dispatched frequently), ScrollTrigger looks for when there hasn't been any "scroll" events fired for about 200ms AND the pointer/mouse isn't pressed on the document/scrollbar.

```
if (ScrollTrigger.isScrolling()) {  // do something if scrolling}
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
