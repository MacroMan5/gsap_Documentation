# static-getRule() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/CSSRulePlugin/methods/static-getRule()](https://gsap.com/docs/v3/Plugins/CSSRulePlugin/methods/static-getRule())  
**Last Updated:** 2025-05-23T00:28:20.527Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-getRule() | GSAP | Docs & Learning

The stylesheet object (or an array of them if you define only a pseudo element selector like `::before`).

Provides a simple way to find the style sheet object associated with a particular selector like `.myClass` or `#myID`. You'd use this method to determine the target of your tween.

And you want to tween the color of the `.myClass::before` to `blue`. Make sure you load the CSSRulePlugin.js file and then you can do this:

```
var rule = CSSRulePlugin.getRule(".myClass::before"); //get the rulegsap.to(rule, {duration: 3, cssRule: {color: "#0000FF"}});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
