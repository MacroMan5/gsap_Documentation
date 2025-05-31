# gsap.utils | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.utils](https://gsap.com/docs/v3/GSAP/gsap.utils)  
**Last Updated:** 2025-05-23T00:21:17.320Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.utils | GSAP | Docs & Learning

### Type : Object[​](#type--object "Direct link to Type : Object")

Combining utility Methods

GSAP 3 Utility Methods Demo - YouTube

`gsap.utils` provides access to some surprisingly helpful utility functions. Note that many of them can optionally return FUNCTIONS so that they can be plugged directly into tweens, leveraging GSAP's function-based capabilities. In that case, they'll get called once for each target rather than just using the same end value for them all.

| Utility | Description |
| --- | --- |
| [checkPrefix()](https://gsap.com/docs/v3/GSAP/UtilityMethods/checkPrefix\(\)) | Prefixes the provided CSS property if necessary (ex: `checkPrefix("transform")` --> `"msTransform"` when run in IE9; returns null if the property isn't supported at all). |
| [clamp()](https://gsap.com/docs/v3/GSAP/UtilityMethods/clamp\(\)) | Clamp a value to fit within a specific range (ex: `clamp(0, 100, -12)` --> `0`). |
| [distribute()](https://gsap.com/docs/v3/GSAP/UtilityMethods/distribute\(\)) | Distribute a value among an array of objects either linearly or according to their position in a grid, optionally with easing applied. |
| [getUnit()](https://gsap.com/docs/v3/GSAP/UtilityMethods/getUnit\(\)) | Get the unit of a string (ex: `getUnit("30px")` --> `"px"`). |
| [interpolate()](https://gsap.com/docs/v3/GSAP/UtilityMethods/interpolate\(\)) | Interpolate between almost any two values (numbers, colors, strings, arrays, complex strings, or even objects with multiple properties) (ex: `interpolate("red", "blue", 0.5)` --> `"rgba(128,0,128,1)"`). |
| [mapRange()](https://gsap.com/docs/v3/GSAP/UtilityMethods/mapRange\(\)) | Map one range to another (ex: `mapRange(-10, 10, 0, 100, 5)` --> `75`). |
| [normalize()](https://gsap.com/docs/v3/GSAP/UtilityMethods/normalize\(\)) | Map a number within a range to a progress between 0 to 1 (ex: `normalize(100, 200, 150)` --> `0.5`). |
| [`pipe()`](https://gsap.com/docs/v3/GSAP/UtilityMethods/pipe\(\)) | Sequence a number of function calls, passing the result of each into the next (ex: `pipe(clamp(0, 100), snap(5))(8)` --> `10`). |
| [random()](https://gsap.com/docs/v3/GSAP/UtilityMethods/random\(\)) | Generate a random number based on parameters (ex: `random(0, 100, 5)` --> `65`) or randomly pick an element from in a supplied array (ex. `random(["red", "green", "blue"])` --> `"red"`). |
| [selector()](https://gsap.com/docs/v3/GSAP/UtilityMethods/selector\(\)) | Returns a selector **function** that is scoped to a particular Element (or React ref or Angular ElementRef). (ex: `selector(myElement)`) |
| [shuffle()](https://gsap.com/docs/v3/GSAP/UtilityMethods/shuffle\(\)) | Shuffles the contents of an array in-place. (ex: `shuffle([1, 2, 3, 4, 5])` \-\-> `[4, 2, 1, 5, 3]`) |
| [snap()](https://gsap.com/docs/v3/GSAP/UtilityMethods/snap\(\)) | Snap a value to either an increment (ex: `snap(5, 13)` --> `15`) or to the closest value in an array (ex: `snap([0, 5, 10], 7)` --> `5`). |
| [splitColor()](https://gsap.com/docs/v3/GSAP/UtilityMethods/splitColor\(\)) | Split any color into its red, green, blue (and optionally alpha) components. Or hue, saturation, and brightness. (ex: `splitColor("red")` --> `[255, 0, 0]`). |
| [toArray()](https://gsap.com/docs/v3/GSAP/UtilityMethods/toArray\(\)) | Convert almost any array-like object to an array, including selector text! (ex: `toArray(".class")` --> `[element1, element2]`). |
| [unitize()](https://gsap.com/docs/v3/GSAP/UtilityMethods/unitize\(\)) | Wraps around another utility function, allowing it to accept values with units like `"20px"` or `"50%"`, stripping off the unit when feeding into the wrapped utility function, and then adding it back to the result (ex. `var wrap = gsap.utils.unitize( gsap.utils.wrap(0, 100) ); wrap("150px");` --> `"50px"`). Or force a specific unit (ex: `unitize( gsap.utils.mapRange(-10, 10, 0, 100), "%");` --> always returns with `"%"`). |
| [wrap()](https://gsap.com/docs/v3/GSAP/UtilityMethods/wrap\(\)) | Place a number into a specified range such that when it exceeds the maximum, it wraps back to the start and if it is less than the minimum, it wraps to the end (ex. `wrap(5, 10, 12)` --> `7`). Or cycle through an **Array** such that when the provided index is greater than the length of the array, it wraps back to the start (ex: `wrap([0, 10, 20], 4)` --> `10`). |
| [wrapYoyo()](https://gsap.com/docs/v3/GSAP/UtilityMethods/wrapYoyo\(\)) | Place a number into a specified range such that when it exceeds the maximum, it yoyos back toward the start and if it is less than the minimum, it yoyos forward to the end (ex. `wrapYoyo(5, 10, 12)` --> `8`). Or cycle through an **Array** such that when the provided index is greater than the length of the array, it yoyos back to the start (ex: `wrap([0, 10, 20, 30], 4)` --> `20`) |

---

*This documentation was extracted from the database for URLs containing 'gsap'*
