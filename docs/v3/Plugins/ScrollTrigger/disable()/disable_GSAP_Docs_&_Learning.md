# disable | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/disable()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/disable())  
**Last Updated:** 2025-05-23T00:34:02.544Z  
**Extracted:** 2025-05-31 16:56:03

---

# disable | GSAP | Docs & Learning

### .disable( revert:boolean, allowAnimation:Boolean )

Disables the ScrollTrigger instance, immediately unpinning and restoring any pin-related changes made to the DOM by ScrollTrigger.

#### Parameters

*   #### **revert**: boolean
    
    Determines whether or not the elements should be reverted to their pre-ScrollTriggered state after the ScrollTrigger is disabled. `true` by default.
    
*   #### **allowAnimation**: Boolean
    
    By default, any associated scrub animation will be paused but if allowAnimation is true, it won't pause() the animation.
    

### Details[​](#details "Direct link to Details")

Disables the ScrollTrigger instance, immediately unpinning and restoring any pin-related changes made to the DOM by ScrollTrigger. It also reverts the animation (if one is defined), although you can skip that using the first parameter.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
