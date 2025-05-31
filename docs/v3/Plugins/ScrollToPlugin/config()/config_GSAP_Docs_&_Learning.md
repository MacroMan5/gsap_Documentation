# config | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollToPlugin/config()](https://gsap.com/docs/v3/Plugins/ScrollToPlugin/config())  
**Last Updated:** 2025-05-23T00:19:21.440Z  
**Extracted:** 2025-05-31 16:56:03

---

# config | GSAP | Docs & Learning

## ScrollToPlugin.config

### ScrollToPlugin.config( vars:Object )

Allows you to configure the global behavior of ScrollToPlugin like `autoKill`

#### Parameters

*   #### **vars**: Object
    
    A configuration object with the properties you'd like to affect, like `{ autoKill: true }`
    

### Details[​](#details "Direct link to Details")

Allows you to configure the global behavior of ScrollToPlugin like:

*   **autoKill** _\[Boolean\]_ - if `true`, ScrollToPlugin will automatically sense if the scroll position was changed outside of itself (like if the user manually started dragging the scrollbar mid-tween) and cancel that portion of the tween.

### Example[​](#example "Direct link to Example")

```
ScrollToPlugin.config({ autoKill: true })
```

`ScrollToPlugin.config()` was added in version 3.12.6

---

*This documentation was extracted from the database for URLs containing 'gsap'*
