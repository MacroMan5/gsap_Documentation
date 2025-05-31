# VelocityTracker | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/InertiaPlugin/VelocityTracker/](https://gsap.com/docs/v3/Plugins/InertiaPlugin/VelocityTracker/)  
**Last Updated:** 2025-05-23T00:30:49.035Z  
**Extracted:** 2025-05-31 16:56:03

---

# VelocityTracker | GSAP | Docs & Learning

## Description[​](#description "Direct link to Description")

Allows you to have the velocity of particular properties automatically tracked for you so that you can access them anytime using the VelocityTracker's `getVelocity()` method, like `myTracker.getVelocity("y")`.

For example, let's say there's an object that the user interacts with by dragging it or maybe it is being tweened and then at some point you want to create a tween based on that velocity. Normally, you'd need to write your own tracking code that records that object's `x` and `y` properties (as well as time stamps) so that when it comes time to feed the `velocity` into whatever other code you need to run, you'd have the necessary data to calculate it. But let's face it: that can be cumbersome to do manually, and that's precisely why VelocityTracker exists.

VelocityTracker is in the InertiaPlugin JavaScript file. You can access the important methods directly through InertiaPlugin, like `InertiaPlugin.track()`.

Use the static `VelocityTracker.track()` method to start tracking properties. _You generally should **not** use the VelocityTracker's constructor because there needs to only be one VelocityTracker instance associated with any particular object._ The `track()` method will return the instance that you can then use to `getVelocity()` like:

```
// first, start tracking "x" and "y":var tracker = VelocityTracker.track(obj, "x,y")[0];//then, after at least 100ms and 2 "ticks", we can get the velocity of each property:var vx = tracker.get("x");var vy = tracker.get("y");
```

## What kinds of properties can be tracked?[​](#what-kinds-of-properties-can-be-tracked "Direct link to What kinds of properties can be tracked?")

Pretty much any numeric property of any object can be tracked, including function-based ones. For example, `obj.x` or `obj.rotation` or even `obj.myCustomProp()`. In fact, for getters and setters that start with the word "get" or "set" (like `getCustomProp()` and `setCustomProp()`), it will automatically find the matching counterpart method and use the getter appropriately, so you can track the getter or setter and it'll work. You **cannot**, however, track custom plugin-related values like `directionalRotation`, `autoAlpha`, or `physics2D` because those aren't real properties of the object. You should instead track the real properties that those plugins affect, like `rotation`, `alpha`, `x`, or `y`.

This class is used in InertiaPlugin to make it easy to create velocity-based tweens that smoothly transition an object's movement (or rotation or whatever) and glide to a stop.

caution

In order to report accurately, at least 100ms and 2 ticks of the core tweening engine must have been elapsed before you check velocity.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
