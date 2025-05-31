# getDirectionalSnapFunc | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/getDirectionalSnapFunc](https://gsap.com/docs/v3/HelperFunctions/helpers/getDirectionalSnapFunc)  
**Last Updated:** 2025-05-23T00:20:00.606Z  
**Extracted:** 2025-05-31 16:56:03

---

# getDirectionalSnapFunc | GSAP | Docs & Learning

Normally when you snap a value, it goes to the **CLOSEST** one (either an increment or the value in an Array), like:

But what if you want to apply **directional** snapping so that, for example, you want to snap to the closest increment of 5 that's GREATER than the value? You need a function that'll accept a value and a direction where `1` means "greater" and `-1` means "lesser". Here's the helper function:

```
function getDirectionalSnapFunc(snapIncrementOrArray) {  let snap = gsap.utils.snap(snapIncrementOrArray),    a =      Array.isArray(snapIncrementOrArray) &&      snapIncrementOrArray.slice(0).sort((a, b) => a - b);  return a    ? (value, direction) => {        let i;        if (!direction) {          return snap(value);        }        if (direction > 0) {          value -= 1e-4; // to avoid rounding errors. If we're too strict, it might snap forward, then immediately again, and again.          for (i = 0; i < a.length; i++) {            if (a[i] >= value) {              return a[i];            }          }          return a[i - 1];        } else {          i = a.length;          value += 1e-4;          while (i--) {            if (a[i] <= value) {              return a[i];            }          }        }        return a[0];      }    : (value, direction) => {        let snapped = snap(value);        return !direction ||          Math.abs(snapped - value) < 0.001 ||          snapped - value < 0 === direction < 0          ? snapped          : snap(              direction < 0                ? value - snapIncrementOrArray                : value + snapIncrementOrArray            );      };}
```

```
let snap = getDirectionalSnapFunc(5); // returns a function that snaps any value to the closest increment of 5 in a particular directionconsole.log(snap(2, 1)); // 5console.log(snap(3.5, -1)); // 0console.log(snap(19, -1)); // 15
```

Note that you can use an Array of values instead of an increment. Super convenient!

---

*This documentation was extracted from the database for URLs containing 'gsap'*
