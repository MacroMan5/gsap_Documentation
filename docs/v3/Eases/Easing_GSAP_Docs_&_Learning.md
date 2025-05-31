# Easing | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Eases](https://gsap.com/docs/v3/Eases)  
**Last Updated:** 2025-05-23T00:16:33.514Z  
**Extracted:** 2025-05-31 16:56:03

---

# Easing | GSAP | Docs & Learning

**Easing is the primary way to change the timing of your tweens.** Simply changing the ease can adjust the entire feel and personality of your animation. There are infinite eases that you can use in GSAP so we created the visualizer below to help you choose exactly the type of easing that you need.

## Ease Visualizer

*   Add point: ALT-CLICK on line
*   Toggle smooth/corner: ALT-CLICK anchor
*   Get handle from corner anchor: ALT-DRAG
*   Toggle select: SHIFT-CLICK anchor
*   Delete anchor: press DELETE key
*   Undo: CTRL-Z

gsap.to(target,

{

duration:2.5,

ease: "power1.out",

y: \-500

Coding tip - Default Easing

GSAP uses a default ease of `"power1.out"`. You can overwrite this in any tween by setting the `ease` property of that tween to another (valid) ease value. You can set a different default ease for GSAP by using [gsap.defaults()](https://gsap.com/docs/v3/GSAP/gsap.defaults\(\)). You can also set defaults for particular [timelines](https://gsap.com/docs/v3/GSAP/Timeline).

```
gsap.defaults({  ease: "power2.in",  duration: 1,});gsap.timeline({defaults: {ease: "power2.in"}})
```

## How to use the Ease Visualizer[​](#how-to-use-the-ease-visualizer "Direct link to How to use the Ease Visualizer")

To use the ease visualizer, simply click on the ease name that you'd like to use. You can also click on the underlined text to change the values and type of ease.  
Use the navigation links in the menu to the left for more information about complex eases.

Video Walkthrough

GSAP Ease Visualizer - YouTube

Huge thanks to Carl for providing this video. We highly recommend their extensive GSAP training at [CreativeCodingClub.com](https://www.creativecodingclub.com/bundles/creative-coding-club?ref=44f484). Enroll today in their [Free GSAP course](https://www.creativecodingclub.com/courses/FreeGSAP3Express?ref=44f484) and discover the joy of animating with code.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
