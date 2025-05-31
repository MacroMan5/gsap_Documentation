# revert | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/revert()](https://gsap.com/docs/v3/GSAP/Timeline/revert())  
**Last Updated:** 2025-05-23T00:26:45.209Z  
**Extracted:** 2025-05-31 16:56:03

---

# revert | GSAP | Docs & Learning

### revert( ) : Self

Reverts the Timeline and kills it, returning the targets to their pre-animation state including the removal of inline styles added by the Timeline.

### Returns : Self[​](#returns--self "Direct link to Returns : Self")

The Timeline itself, for easy chaining

### Details[​](#details "Direct link to Details")

Reverts the Timeline and kills it, returning the targets to their pre-animation state including the removal of inline styles added by the Timeline.

## The problem[​](#the-problem "Direct link to The problem")

What if you want to revert an element back to its state **BEFORE** it was animated? You could just `animation.progress(0)`, right? _Sort of_. Consider this element:

**No inline styles at all**. The opacity is 1 (the default) and then you do this:

```
// fade outlet tl = gsap.timeline();tl.to(".box", { opacity: 0 });
```

Now let's try getting back to the original state:

That does indeed set it back to the starting values that GSAP parsed from the computed style:

```
<!-- inline style is still present --><div class="box" style="opacity: 1"></div>
```

But that means **it** **still has inline styles**. Usually that doesn't matter, but perhaps a media query CSS rule sets opacity to 0.5 on that element. Doh! The inline style will overrule the class rule. So we need a way to have a tween/timeline keep track of the original inline styles and **REMOVE** the ones that it added. That requires a new method because `progress(0)` _SHOULD_ set inline styles to ensure the state is what it's supposed to be at that point in the animation.

### The solution: revert()[​](#the-solution-revert "Direct link to The solution: revert()")

GSAP 3.11 added a `.revert()` method to all Tweens and Timelines, so it's as simple as:

```
tl.revert(); // removes inline styles that were added by the animation
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
