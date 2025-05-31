# split | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/SplitText/split()](https://gsap.com/docs/v3/Plugins/SplitText/split())  
**Last Updated:** 2025-05-23T00:35:03.141Z  
**Extracted:** 2025-05-31 16:56:03

---

# split | GSAP | Docs & Learning

### split( vars:Object ) ;

\[static\] Splits the text in the target element(s) according to the provided config properties.

#### Parameters

*   #### **vars**: Object
    
    (default = `null`) - a configuration object defining any of the following values: `type, charsClass, wordsClass, linesClass`, or `position`. (see the constructor description for details)
    

### Details[​](#details "Direct link to Details")

Splits the text in the target element(s) according to the provided config properties. Normally you don't need to use this method because it is called in the constructor automatically, but if you want to **change** the way the text is split after the SplitText instance is created, you can use this method. It will automatically call `revert()` first if necessary.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
