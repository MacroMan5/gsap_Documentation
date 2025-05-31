# parent | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/parent](https://gsap.com/docs/v3/GSAP/Timeline/parent)  
**Last Updated:** 2025-05-23T00:25:17.636Z  
**Extracted:** 2025-05-31 16:56:03

---

# parent | GSAP | Docs & Learning

### parent : Timeline

The parent [Timeline](https://gsap.com/docs/v3/GSAP/Timeline) to which the animation is attached. Anything that's not in a Timeline that you create is placed on the [gsap.globalTimeline](https://gsap.com/docs/v3/GSAP/gsap.globalTimeline) by default.

### Details[​](#details "Direct link to Details")

The parent [Timeline](https://gsap.com/docs/v3/GSAP/Timeline) to which the Timeline is attached. Anything that's not inside a Timeline that you create is placed on the [gsap.globalTimeline](https://gsap.com/docs/v3/GSAP/gsap.globalTimeline\(\)) by default.

Each animation ([Tweens](https://gsap.com/docs/v3/GSAP/Tween) and [Timelines](https://gsap.com/docs/v3/GSAP/Timeline)) can only exist in one parent. Think of it like a DOM element that can't have multiple parents. If you [add()](https://gsap.com/docs/v3/GSAP/Timeline/add\(\)) an animation to a different Timeline, its `parent` will change to that Timeline.

## How do timelines work?[​](#how-do-timelines-work "Direct link to How do timelines work?")

See the [Timeline docs for details](https://gsap.com/docs/v3/GSAP/Timeline#mechanics). It's very helpful to understand how the mechanics work conceptually.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
