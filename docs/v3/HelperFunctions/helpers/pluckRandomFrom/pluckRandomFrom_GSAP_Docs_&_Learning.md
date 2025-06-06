# pluckRandomFrom | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/pluckRandomFrom](https://gsap.com/docs/v3/HelperFunctions/helpers/pluckRandomFrom)  
**Last Updated:** 2025-05-23T00:20:37.863Z  
**Extracted:** 2025-05-31 16:56:03

---

# pluckRandomFrom | GSAP | Docs & Learning

Randomly pluck values from an array one-by-one until they've all been plucked (almost as if when you pluck one, it's no longer available to be plucked again until ALL of them have been uniquely plucked):

```
function pluckRandomFrom(array) {  return (    array.eligible && array.eligible.length      ? array.eligible      : (array.eligible = gsap.utils.shuffle(array.slice(0)))  ).pop();}
```

All you've gotta do is feed the array in each time and it keeps track of things for you!

Alternatively, if you just want to pull a random element from an array that's not the PREVIOUS one that was pulled (so not emptying the array, just pulling randomly while ensuring the same element isn't pulled twice in a row), you can use this:

---

*This documentation was extracted from the database for URLs containing 'gsap'*
