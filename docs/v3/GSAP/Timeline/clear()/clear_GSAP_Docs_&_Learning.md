# clear | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/clear()](https://gsap.com/docs/v3/GSAP/Timeline/clear())  
**Last Updated:** 2025-05-23T00:25:53.112Z  
**Extracted:** 2025-05-31 16:56:03

---

# clear | GSAP | Docs & Learning

### clear( labels:Boolean ) : self

Empties the timeline of all tweens, timelines, and callbacks (and optionally labels too).

#### Parameters

*   #### **labels**: Boolean
    
    (default = `true`) - If `true` (the default), labels will be cleared too.
    

### Returns : self[​](#returns--self "Direct link to Returns : self")

self (makes chaining easier)

### Details[​](#details "Direct link to Details")

Empties the timeline of all tweens, timelines, and callbacks (and optionally labels too). Event callbacks (like onComplete, onUpdate, onStart, etc.) are not removed. If you need to remove event callbacks, use the `eventCallback()` method and set them to null like `myTimeline.eventCallback("onComplete", null);`

---

*This documentation was extracted from the database for URLs containing 'gsap'*
