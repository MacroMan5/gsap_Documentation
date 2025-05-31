# Plugins | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/](https://gsap.com/docs/v3/Plugins/)  
**Last Updated:** 2025-05-24T13:14:46.323Z  
**Extracted:** 2025-05-31 16:56:03

---

# Plugins | GSAP | Docs & Learning

At the end of the day, all the plugins are just JS files - just like the core library. You can install them with script tags, via npm, with yarn, or even with a tgz file.

Registering a plugin with the GSAP core ensures that the two work seamlessly together and also prevents tree shaking issues in build tools/bundlers. You only need to register a plugin once before using it, like:

```
//list as many as you'd likegsap.registerPlugin(MotionPathPlugin, ScrollTrigger, MorphSVGPlugin);
```

Obviously you need to load the plugin file first. There is no harm in registering the same plugin multiple times (but it doesn't help either).

---

*This documentation was extracted from the database for URLs containing 'gsap'*
