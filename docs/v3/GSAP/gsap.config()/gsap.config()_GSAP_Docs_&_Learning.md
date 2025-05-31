# gsap.config() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.config()](https://gsap.com/docs/v3/GSAP/gsap.config())  
**Last Updated:** 2025-05-23T00:21:24.545Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.config() | GSAP | Docs & Learning

`gsap.config()` lets you configure GSAP's settings that aren't Tween-specific, like `autoSleep`, `force3D`, and `units`. To affect properties that should be **inherited** by individual tweens, use [`gsap.defaults()`](https://gsap.com/docs/v3/GSAP/gsap.defaults\(\)) instead. Here is a list of config() options:

```
// you only need to define the configuration settings you want to CHANGE. Omitted properties won't be affected.gsap.config({  autoSleep: 60,  force3D: false,  nullTargetWarn: false,  trialWarn: false,  units: { left: "%", top: "%", rotation: "rad" },});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
