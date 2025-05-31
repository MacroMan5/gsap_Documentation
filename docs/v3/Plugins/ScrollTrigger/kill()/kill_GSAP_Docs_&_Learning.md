# kill | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/kill()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/kill())  
**Last Updated:** 2025-05-23T00:34:19.014Z  
**Extracted:** 2025-05-31 16:56:03

---

# kill | GSAP | Docs & Learning

### .kill( revert:boolean, allowAnimation:Boolean )

Kills the ScrollTrigger instance, immediately unpinning and restoring any pin-related changes made to the DOM by ScrollTrigger and removing all scroll-related listeners, etc. so that the instance is eligible for garbage collection. If you only want to temporarily disable the ScrollTrigger, use the [disable()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/disable\(\)) method instead.

#### Parameters

*   #### **revert**: boolean
    
    Determines whether or not the elements should be reverted to their pre-ScrollTriggered state after the ScrollTrigger is killed. `true` by default.
    
*   #### **allowAnimation**: Boolean
    
    By default, any associated animation will be killed but if `allowAnimation` is `true`, it won't kill() the animation.
    

### Details[​](#details "Direct link to Details")

Kills the ScrollTrigger instance, immediately unpinning and restoring any pin-related changes made to the DOM by ScrollTrigger and removing all scroll-related listeners, etc. so that the instance is eligible for garbage collection. If you only want to temporarily disable the ScrollTrigger, use the [disable()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/disable\(\)) method instead.

To prevent the animation from being reverted when it is killed, simply pass false as the parameter. For example ST.kill(false).

---

*This documentation was extracted from the database for URLs containing 'gsap'*
