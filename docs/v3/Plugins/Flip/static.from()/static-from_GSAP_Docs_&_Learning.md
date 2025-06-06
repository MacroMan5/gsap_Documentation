# static-from | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Flip/static.from()](https://gsap.com/docs/v3/Plugins/Flip/static.from())  
**Last Updated:** 2025-05-23T00:30:09.859Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-from | GSAP | Docs & Learning

```
<div class="initial">
  <img class="thumbnail" data-flip-id="img" src="https://assets.codepen.io/16327/flip-flair.png">
</div>

<div class="container">
  <img class="full-size" data-flip-id="img"  src="https://assets.codepen.io/16327/massive-flip-flair.png">
</div>
```

```
body {
  padding: 0;
  box-sizing: border-box;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  height: 100vh;
  overflow: hidden;
}
h1 {
  margin-left: 20px;
}

.container {
  position: fixed;
  top: 15px;
  left: 15px;
  right: 15px;
  bottom: 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  align-content: center;
  pointer-events: none;
  z-index: 999;
}

.full-size {
  position: relative;
  flex-shrink: 0;
  flex-grow: 0;
  height: 80%;
  aspect-ratio: 1/1;
  display: none;
}
.full-size.active {
  display: block;
  z-index: 2;
}

.thumbnail {
  width: 150px;
  height: 150px;
}

.initial {
  position: relative;
  width: 180px;
  height: 180px;
  border: dashed 2px var(--color-surface-white);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1;
}

.initial:after {
  content: "drag and click me...";
  position: absolute;
  background-image: url("data:image/svg+xml,%3Csvg width='100%25' height='100%25' viewBox='0 0 1516 1464' version='1.1' xmlns='http://www.w3.org/2000/svg' xmlns:xlink='http://www.w3.org/1999/xlink' xml:space='preserve' xmlns:serif='http://www.serif.com/' style='fill-rule:evenodd;clip-rule:evenodd;stroke-linejoin:round;stroke-miterlimit:2;'%3E%3Cpath d='M481.106,1059.48c40.533,-60.792 74.612,-125.5 105.72,-191.542c33.38,-70.875 64.242,-142.917 98.3,-213.458c33.85,-70.084 70.951,-139 116.609,-202.209c4.479,-6.208 9.108,-12.333 13.75,-18.416c36.487,-46.334 78.041,-88.125 124.45,-124.542c64.5,-48.917 136.066,-87.458 210.354,-119.333c83.954,-35.042 170.958,-62.167 258.404,-87.042c25.217,-7.167 50.479,-14.125 75.754,-21.083c21.009,-5.792 36.03,-29.834 29.1,-51.25c-6.954,-21.5 -28.737,-35.292 -51.254,-29.125c-100.741,27.708 -201.579,56.041 -299.054,93.958c-101.329,39.417 -197.683,88.458 -283.421,155.792c-84.475,66.375 -151.204,151.666 -205.071,244.125c-53.637,92.042 -95.441,190.25 -139.691,286.958c-41.634,91 -86.405,180.75 -144.725,262.375c-5.73,8.042 -11.613,15.958 -17.588,23.792c-34.783,44.375 -73.808,85.5 -118.171,120.458c-31.387,23.583 -65.154,43.792 -101.121,59.584c-3.295,1.333 -6.608,2.625 -9.929,3.916c29.221,-57.958 56.104,-117.166 79.171,-177.792c15.171,-39.874 28.579,-80.583 37.846,-122.249c2.421,-10.875 1.529,-22.334 -4.2,-32.126c-5.058,-8.625 -14.967,-16.875 -24.9,-19.124c-10.667,-2.459 -22.642,-1.917 -32.108,4.166c-8.871,5.75 -16.788,14.292 -19.15,24.917c-12.555,56.458 -32.48,111.166 -54.746,164.5c-19.3,45.333 -40.504,89.875 -63.046,133.708c-15.325,29.792 -31.233,59.292 -47.879,88.375c-2.946,5.167 -5.9,10.292 -8.938,15.417c-6.841,11.458 -7.191,25 -2.1,37.083c4.634,10.959 14.567,21.917 27,24.125c102.446,18 204.888,36 307.329,54c28.688,5.042 57.371,10.083 86.055,15.125c11.287,1.959 21.891,1.75 32.104,-4.208c8.646,-5.084 16.887,-14.959 19.15,-24.917c2.429,-10.666 1.904,-22.625 -4.2,-32.083c-5.563,-8.625 -14.379,-17.334 -24.9,-19.167c-93.467,-16.416 -186.929,-32.833 -280.392,-49.25c62.683,-23.708 119.513,-59.458 170.283,-103.5c56.417,-48.916 103.888,-107.958 145.205,-169.958Z' style='fill:%23fffce1;fill-rule:nonzero;'/%3E%3C/svg%3E");
  width:200px;
  height: 72px;
  background-size: 60px;
  padding-left: 75px;
  background-position: bottom left;
  background-repeat: no-repeat;
  text-align: left;
  bottom: 100%;
  margin-bottom: 0.2rem;
  margin-left: 0.5rem;
  left: 100%;
}

.thumbnail.active {
  visibility: hidden;
}
.thumbnail,
.thumbnail.flipping {
  visibility: visible;
}
```

```
gsap.registerPlugin(Flip, Draggable);

const fullSize = document.querySelector(".full-size"),
      thumbnail = document.querySelector(".thumbnail");

Draggable.create(".initial", {bounds: "body"});

document.addEventListener("click", () => {
  const state = Flip.getState(".thumbnail, .full-size");

  fullSize.classList.toggle("active");
  thumbnail.classList.toggle("active");

  Flip.from(state, {
    duration: 0.6,
    fade: true,
    absolute: true,
    toggleClass: "flipping",
    ease: "power1.inOut"
  });
  
});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
