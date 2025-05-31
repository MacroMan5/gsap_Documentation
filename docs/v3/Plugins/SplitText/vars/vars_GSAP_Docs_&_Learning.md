# vars | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/SplitText/vars](https://gsap.com/docs/v3/Plugins/SplitText/vars)  
**Last Updated:** 2025-05-23T00:34:49.826Z  
**Extracted:** 2025-05-31 16:56:03

---

# vars | GSAP | Docs & Learning

```
let splitText = SplitText.create({  type: "chars,words",  wordsClass: "word++",});console.log(splitText.vars); // {type: "chars,words",wordsClass: "word++",}
```

You can store arbitrary data in the `vars` object if you want; SplitText will just ignore the properties it doesn't recognize. So, for example, you could add a "group" property so that you could group your Splits and then later to kill() all the SplitText instances from a particular group, you could do:

---

*This documentation was extracted from the database for URLs containing 'gsap'*
