# gsap.updateRoot() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.updateRoot()](https://gsap.com/docs/v3/GSAP/gsap.updateRoot())  
**Last Updated:** 2025-05-23T00:21:01.707Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.updateRoot() | GSAP | Docs & Learning

Normally GSAP handles all of its timing internally using a `requestAnimationFrame` loop (or falls back to `setTimeout()` if rAF isn't available), but some game developers requested a way to manually update the root (global) timeline which is exactly what `gsap.updateRoot()` permits. This is only intended for **advanced** users. First, you'd need to unhook GSAP's ticker like this:

```
//unhooks the GSAP tickergsap.ticker.remove(gsap.updateRoot);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
