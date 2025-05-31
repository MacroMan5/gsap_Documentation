# progressiveBuild | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/progressiveBuild](https://gsap.com/docs/v3/HelperFunctions/helpers/progressiveBuild)  
**Last Updated:** 2025-05-23T00:20:45.215Z  
**Extracted:** 2025-05-31 16:56:03

---

# progressiveBuild | GSAP | Docs & Learning

Maybe you can't pre-build your entire timeline because you need to call individual functions in a sequenced fashion. Perhaps they each change the state of elements, creating an animation that must finish before the next step (function) is called. This helper function lets you organize your code quite easily into a simple sequence of arguments you pass, and you can even have a delay between each step:

```
function progressiveBuild() {  let data = Array.from(arguments),    i = 0,    tl = gsap.timeline({      onComplete: function () {        let isNum = typeof data[i] === "number",          delay = isNum ? data[i++] : 0,          func = data[i++];        typeof func === "function" && tl.add(func(), "+=" + delay);      },    });  tl.vars.onComplete();  return tl;}
```

```
progressiveBuild(  step1,  step2,  1.5, // 1.5-second delay (sprinkle between any two functions)  step3);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
