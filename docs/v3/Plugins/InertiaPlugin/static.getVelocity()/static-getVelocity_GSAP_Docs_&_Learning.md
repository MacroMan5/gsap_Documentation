# static-getVelocity | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/InertiaPlugin/static.getVelocity()](https://gsap.com/docs/v3/Plugins/InertiaPlugin/static.getVelocity())  
**Last Updated:** 2025-05-23T00:30:34.020Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-getVelocity | GSAP | Docs & Learning

Returns the current velocity of the given property and target object (only works if you started tracking the property using the [`InertiaPlugin.track()`](https://gsap.com/docs/v3/Plugins/InertiaPlugin/static.track\(\)) method).

```
// track the x and y properties:InertiaPlugin.track("#box", "x,y");// then later, get the velocity:let velocityX = InertiaPlugin.getVelocity("#box", "x");
```

For maximum performance, you can just keep the VelocityTracker object that gets returned by the .track() call and get the velocity directly through that:

```
// track the x and y properties, but this time keep a reference to the VelocityTracker instance:const tracker = InertiaPlugin.track("#box", "x,y")[0];// then later, get the velocity:let velocityX = tracker.get("x"),  velocityY = tracker.get("y");
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
