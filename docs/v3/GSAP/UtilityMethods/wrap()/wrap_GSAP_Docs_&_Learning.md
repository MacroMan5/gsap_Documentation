# wrap | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/UtilityMethods/wrap()](https://gsap.com/docs/v3/GSAP/UtilityMethods/wrap())  
**Last Updated:** 2025-05-23T00:13:54.646Z  
**Extracted:** 2025-05-31 16:56:03

---

# wrap | GSAP | Docs & Learning

Returns the next item in an array or number in a range after the given index. Or returns a function that returns that object or value if no index is given.

Places a number (or index of an Array) into a specified range such that when it exceeds the maximum, it wraps back to the start and if it is less than the minimum, it wraps to the end. In the context of tweening this has the effect of cycling through the values.

For example, if you have 10 elements with the `"box"` class applied, and you've got a `["red", "green", "yellow"]` array of colors that you'd like to have those elements animate to so that the first box animates to `"red"`, then next to `"green"`, then next to `"yellow"` and then wrap around again so that the 4th would go to `"red"`, 5th to `"green"`, etc., `wrap()` is perfect for that. If we don't provide an `index` value, we'll get a `function` instead that's ready to do wrapping accordingly.

```
//returns the corresponding value in the array (wrapping back to the beginning when necessary)let color = gsap.utils.wrap(["red", "green", "yellow"], 5); // "yellow" (index 5 maps to index 2 in a 3-element Array)//or use a rangelet num = gsap.utils.wrap(5, 10, 12); // 7 (12 is two more than the max of 10, so it wraps around to the start and goes two up from there)//if we don't provide an index, we get a function that's ready to do wrapping accordinglylet wrapper = gsap.utils.wrap(["red", "green", "yellow"]);//now we just feed an index number into the function we got back from the line above and we'll get the corresponding value from the wrapped Arraylet color = wrapper(5) // "yellow"
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
