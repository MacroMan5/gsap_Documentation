# static-saveStyles | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.saveStyles()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.saveStyles())  
**Last Updated:** 2025-05-23T00:33:36.209Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-saveStyles | GSAP | Docs & Learning

Internally records the current inline CSS styles for the given elements so that when ScrollTrigger reverts (typically for a [refresh()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.refresh\(\)) or [matchMedia()](https://gsap.com/docs/v3/Plugins/ScrollTrigger/static.matchMedia\(\)) change) those elements will be reverted accordingly even if they had animations that added/changed inline styles. Think of it like taking a snapshot of the inline CSS and telling ScrollTrigger _"re-apply these inline styles only and dump all others when you revert internally"_.

```
ScrollTrigger.saveStyles(".panel, #logo");
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
