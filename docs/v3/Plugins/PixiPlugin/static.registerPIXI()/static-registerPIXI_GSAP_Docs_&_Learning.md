# static-registerPIXI | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/PixiPlugin/static.registerPIXI()](https://gsap.com/docs/v3/Plugins/PixiPlugin/static.registerPIXI())  
**Last Updated:** 2025-05-23T00:32:48.551Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-registerPIXI | GSAP | Docs & Learning

PixiPlugin needs some reference to the PIXI library object (usually `PIXI`), which it looks for in the global scope (`window` in most cases). However in a build system or ES module environment you might not have a global scope that has a reference to your `PIXI` object. That's where this method is useful. You can simply pass in that reference using this method like:

When importing individual Pixi.js modules, you can pass in the plugin's dependencies as an object.

```
import { gsap } from "gsap";import { PixiPlugin } from "gsap/PixiPlugin";import { Container, Sprite, BlurFilter, ColorMatrixFilter } from "https://cdn.skypack.dev/pixi.js";PixiPlugin.registerPIXI({  Container,  Sprite,  BlurFilter,  ColorMatrixFilter});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
