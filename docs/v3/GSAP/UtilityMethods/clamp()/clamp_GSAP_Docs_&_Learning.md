# clamp | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/UtilityMethods/clamp()](https://gsap.com/docs/v3/GSAP/UtilityMethods/clamp())  
**Last Updated:** 2025-05-23T00:15:28.510Z  
**Extracted:** 2025-05-31 16:56:03

---

# clamp | GSAP | Docs & Learning

Clamps a number between a given minimum and maximum. If the number you provide is less than the minimum, it will return the minimum. If it's greater than the maximum, it returns the maximum. If it's between the minimum and maximum, it returns the number unchanged.

* * *

#### loading...

  CodePen Embed - gsap.utils.clamp()  

```
<svg viewBox="-1 -1 102 20">
  <rect width="100" height="10" rx="5" stroke="rgb(255, 252, 225)" />
  <rect width="50" height="10" x="25" stroke="rgb(255, 252, 225)"/>
  <rect id="ball" width="6" height="6" rx="3" y="2" fill="#0AE448"/>
</svg>

<input id="num" type="text" maxlength="8" value="50"/>

<p>Type a number above.<br>The value will be clamped between 30 & 70.</p>
```

```
html, body {
  margin:0;
  padding:0;
  width:100%;
  height:100vh;
}

body {
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
}

svg {
  width:50%;
  max-width:750px;
}

input {
  text-align:center;
  font-size:2rem;
  background:transparent;
  border:none;
  border-bottom:1px solid rgb(255, 252, 225);
  color:rgb(255, 252, 225);
  width:90px;
  padding: .2rem;
  outline:none;
}

p {
  text-align:center;
  line-height:2rem;
  font-size:1.3rem;
}
```

```
gsap.set('#ball', { xPercent:-50, x:50 })

const num = document.querySelector("#num");

window.addEventListener("keyup", (e)=>{
  gsap.set('#ball', {
    x: gsap.utils.clamp(30, 70, num.value)
  })
})
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

Choose one of the following method signatures - either get a clamped value immediately or omit the `valueToClamp` parameter to get a **reusable function** that remembers the minimum/maximum so that you can feed in values to clamp later as many times as you want:

## 1) clamp(minimum, maximum, valueToClamp)[​](#1-clampminimum-maximum-valuetoclamp "Direct link to 1) clamp(minimum, maximum, valueToClamp)")

1.  **minimum** : Number - The minimum value
2.  **maximum** : Number - The maximum value
3.  **valueToClamp** : Number - The value that should be clamped between the first two values.

**Returns**: the clamped number

#### Example[​](#example "Direct link to Example")

```
// set the clamping range to between 0 and 100, and clamp 105gsap.utils.clamp(0, 100, 105); // returns 100// in the same range, clamp -50gsap.utils.clamp(0, 100, -50); // returns 0// and clamp 20gsap.utils.clamp(0, 100, 20); // returns 20
```

## 2) clamp(minimum, maximum)[​](#2-clampminimum-maximum "Direct link to 2) clamp(minimum, maximum)")

1.  **minimum** : Number - The minimum value
2.  **maximum** : Number - The maximum value

**Returns**: a reusable function that accepts 1 parameter - a value to clamp

If you omit the `valueToClamp` (3rd) parameter, the utility method will return a **reusable function** that's ready to clamp any value according to the minimum/maximum values provided initially. In other words, the returned function remembers the minimum and maximum values so that it can very quickly and efficiently do the clamping later as many times as you want.

#### Example[​](#example-1 "Direct link to Example")

```
// get a clamping function that will always clamp to a range between 0 and 100var clamper = gsap.utils.clamp(0, 100); // notice we didn't provide a valueToClamp// now we can reuse the function to clamp any values:console.log(clamper(105)); // 100console.log(clamper(-50)); // 0console.log(clamper(20)); // 20
```

## Tip: combine reusable functions for powerful data transformations![​](#tip-combine-reusable-functions-for-powerful-data-transformations "Direct link to Tip: combine reusable functions for powerful data transformations!")

You can [`pipe()`](https://gsap.com/docs/v3/GSAP/UtilityMethods/pipe\(\)) several reusable functions together to perform multiple tasks on an incoming value, like [clamping](https://gsap.com/docs/v3/GSAP/UtilityMethods/clamp\(\)), [mapping](https://gsap.com/docs/v3/GSAP/UtilityMethods/mapRange\(\)) to another range, [snapping](https://gsap.com/docs/v3/GSAP/UtilityMethods/snap\(\)), [interpolating](https://gsap.com/docs/v3/GSAP/UtilityMethods/interpolate\(\)), and [more](https://gsap.com/docs/v3/GSAP/UtilityMethods). For example:

```
// get a clamping function that will always clamp to a range between 0 and 100var transformer = gsap.utils.pipe(  // clamp between 0 and 100  gsap.utils.clamp(0, 100),  // then map to the corresponding position on the width of the screen  gsap.utils.mapRange(0, 100, 0, window.innerWidth),  // then snap to the closest increment of 20  gsap.utils.snap(20));// now we feed one value in and it gets run through ALL those transformations!:transformer(25.874);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
