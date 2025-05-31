# static-clearScrollMemory | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.clearScrollMemory()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.clearScrollMemory())  
**Last Updated:** 2025-05-23T00:34:34.507Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-clearScrollMemory | GSAP | Docs & Learning

## ScrollTrigger.clearScrollMemory

### ScrollTrigger.clearScrollMemory( scrollRestoration:String )

Clears any recorded scroll positions in ScrollTrigger so that no scroll positions get restored after a refresh(). Normally, this isn't necessary but in some frameworks that handle routing in unconventional ways, it can be useful.

#### Parameters

*   #### **scrollRestoration**: String
    
    If you'd like to explicitly set the [window.history.scrollRestoration](https://developer.mozilla.org/en-US/docs/Web/API/History/scrollRestoration) value, you can define `"auto"` or `"manual"`. By default it will use whatever it was when ScrollTrigger loaded.
    

### Details[​](#details "Direct link to Details")

Clears any recorded scroll positions in ScrollTrigger so that no scroll positions get restored after a refresh(). Normally, this isn't necessary but in some frameworks that handle routing in unconventional ways, it can be useful.

You might also want to consider setting `window.history.scrollRestoration = "manual"` to prevent the browser from trying to restore the scroll position from its history (unrelated to ScrollTrigger). See [https://developer.mozilla.org/en-US/docs/Web/API/History/scrollRestoration](https://developer.mozilla.org/en-US/docs/Web/API/History/scrollRestoration)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
