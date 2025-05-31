# static-create | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/SplitText/static.create()](https://gsap.com/docs/v3/Plugins/SplitText/static.create())  
**Last Updated:** 2025-05-23T00:30:23.907Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-create | GSAP | Docs & Learning

Creates a new standalone SplitText instance.

```
SplitText.create(".headline", {  type: "lines,words",  linesClass: "line",  wordsClass: "word++",  autoSplit: true,  onSplit: (self) => {    return gsap.from(self.lines, {      yPercent: 100,      opacity: 0,      stagger: 0.1    });  }});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
