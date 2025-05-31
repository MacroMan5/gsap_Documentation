# random | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/UtilityMethods/random()](https://gsap.com/docs/v3/GSAP/UtilityMethods/random())  
**Last Updated:** 2025-05-23T00:15:57.037Z  
**Extracted:** 2025-05-31 16:56:03

---

# random | GSAP | Docs & Learning

Get a random number within a range (optionally rounding to an increment you provide), or a random element in an array.

* * *

Choose one of the following method signatures - either get a random value immediately or set the the `returnFunction` parameter to `true` to get a **reusable function** that returns a random value according to the range (or array) originally provided each time you call it:

## 1) random(minimum, maximum_\[, snapIncrement, returnFunction\]_)[​](#1-randomminimum-maximum-snapincrement-returnfunction "Direct link to 1-randomminimum-maximum-snapincrement-returnfunction")

1.  **minimum** : Number - The minimum value
2.  **maximum** : Number - The maximum value
3.  **snapIncrement** : Number (optional) - A snapping increment. For example, a value of 5 means the random number would snap to the closest increment of 5
4.  **returnFunction** : Boolean (optional) - If `true`, a reusable function will be returned instead of a random value. This function can be called anytime to randomly choose a value from the range originally provided.

**Returns**: a random value between `minimum` and `maximum`, or if `returnFunction` is `true`, a reusable function that can be called anytime to get a value randomly chosen from the range originally provided

#### Example[​](#example "Direct link to Example")

```
// get a random number between -100 and 100 (no snapping)gsap.utils.random(-100, 100);// a random number between 0 and 500 that's snapped to the closest increment of 5gsap.utils.random(0, 500, 5);// get a reusable function that will randomly choose a value between -200 and 500, snapping to an increment of 10var random = gsap.utils.random(-200, 500, 10, true);// now we can call it anytime:console.log(random()); // random value between -200 and 500, snapping to the closest 10console.log(random()); // another random value between -200 and 500, snapping to the closest 10
```

## 2) random(array_\[, returnFunction\]_)[​](#2-randomarray-returnfunction "Direct link to 2-randomarray-returnfunction")

1.  **array** : Array - An array of values to randomly choose from
2.  **returnFunction** : Boolean (optional) - If `true`, a reusable function will be returned instead of a random value. This function can be called anytime to randomly choose a value from the array originally provided.

**Returns**: a value randomly chosen from the `array`, or if `returnFunction` is `true`, a reusable function that can be called anytime to get a value randomly chosen from the `array`

#### Example[​](#example-1 "Direct link to Example")

```
// get a random value from an array of colorsgsap.utils.random(["red", "blue", "green"]); //"red", "blue", or "green"// get a reusable function that will randomly choose a value from the array of colorsvar random = gsap.utils.random([0, 100, 200], true);// now we can call it anytime:console.log(random()); // 0, 100, or 200 (randomly selected)console.log(random()); // 0, 100, or 200 (randomly selected again)
```

## 3) random(minimum, maximum_\[, returnFunction\]_)[​](#3-randomminimum-maximum-returnfunction "Direct link to 3-randomminimum-maximum-returnfunction")

1.  **minimum** : Number - The minimum value
2.  **maximum** : Number - The maximum value
3.  **returnFunction** : Boolean (optional) - If `true`, a reusable function will be returned instead of a random value. This function can be called anytime to randomly choose a value from the range originally provided.

**Returns**: a random value between `minimum` and `maximum`, or if `returnFunction` is `true`, a reusable function that can be called anytime to get a value randomly chosen from the range originally provided

This is identical it method signature 1 except that it omits the `snapIncrement` for convenience.

#### Example[​](#example-2 "Direct link to Example")

```
// get a random number between 0 and 100 (no snapping)gsap.utils.random(0, 100);// get a reusable function that will randomly choose a value between -10 and 50var random = gsap.utils.random(-10, 50, true);// now we can call it anytime:console.log(random()); // random value between -10 and 50console.log(random()); // another random value between -10 and 50
```

## Tip: combine reusable functions for powerful data transformations![​](#tip-combine-reusable-functions-for-powerful-data-transformations "Direct link to Tip: combine reusable functions for powerful data transformations!")

You can [`pipe()`](https://gsap.com/docs/v3/GSAP/UtilityMethods/pipe\(\)) several reusable functions together to perform multiple tasks on an incoming value, like [clamping](https://gsap.com/docs/v3/GSAP/UtilityMethods/clamp\(\)), [mapping](https://gsap.com/docs/v3/GSAP/UtilityMethods/mapRange\(\)) to another range, [snapping](https://gsap.com/docs/v3/GSAP/UtilityMethods/snap\(\)), [interpolating](https://gsap.com/docs/v3/GSAP/UtilityMethods/interpolate\(\)), and [more](https://gsap.com/docs/v3/GSAP/UtilityMethods). For example:

```
// get a clamping function that will always clamp to a range between 0 and 100var colorizer = gsap.utils.pipe(  // clamp between 0 and 100  gsap.utils.clamp(0, 100),  // normalize to a value between 0 and 1  gsap.utils.normalize(0, 100),  // then interpolate between red and blue  gsap.utils.interpolate("red", "blue"));// now we feed one value in and it gets run through ALL those transformations!:colorizer(25.874);
```

### Video demo: combining utility methods[​](#video-demo-combining-utility-methods "Direct link to Video demo: combining utility methods")

### String form[​](#string-form "Direct link to String form")

Note that inside of tween vars you can also use a string form like `"random(-100, 100)"` for a range or like `"random([red, blue, green])"`. For example:

```
gsap.to(".class", {  x: "random([0, 100, 200, 500])", //randomly selects one of the values (0, 100, 200, or 500)});
```

You can even have the random number rounded to the closest increment of any number! For example:

```
gsap.to(".class", {  x: "random(-100, 100, 5)", //chooses a random number between -100 and 100 for each target, rounding to the closest 5!});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
