# static-addEventListener | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.addEventListener()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.addEventListener())  
**Last Updated:** 2025-05-23T00:34:34.311Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-addEventListener | GSAP | Docs & Learning

## ScrollTrigger.addEventListener

### ScrollTrigger.addEventListener( type:String, callback:Function ) : null

Add a listener for any of the following events: "scrollStart", "scrollEnd", "refreshInit", "revert", "matchMedia", or"refresh" which get dispatched globally when **any** such ScrollTrigger-related event occurs (it is not tied to a particular instance).

#### Parameters

*   #### **type**: String
    
    Event type which may be "scrollStart", "scrollEnd", "refreshInit", "revert", "matchMedia", or "refresh".
    
*   #### **callback**: Function
    
    The function to call when the event occurs
    

These events get dispatched _globally_ when **any** such ScrollTrigger-related event occurs (it is not tied to a particular instance).

```
ScrollTrigger.addEventListener("scrollEnd", () =>  console.log("scrolling ended!"));
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
