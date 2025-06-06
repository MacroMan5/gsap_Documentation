# ExpoScaleEase | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Eases/ExpoScaleEase](https://gsap.com/docs/v3/Eases/ExpoScaleEase)  
**Last Updated:** 2025-05-23T00:14:25.233Z  
**Extracted:** 2025-05-31 16:56:03

---

# ExpoScaleEase | GSAP | Docs & Learning

```
<div id="container">
  <div id="expo">
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-1.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-2.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-3.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-4.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-5.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-6.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-7.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-8.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-9.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-10.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-11.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-12.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-13.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-14.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-15.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-16.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-17.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-18.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-19.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-20.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-21.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-22.jpg" />
    <div class="label">ExpoScaleEase</div>
  </div>


  <div id="linear">
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-1.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-2.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-3.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-4.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-5.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-6.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-7.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-8.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-9.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-10.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-11.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-12.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-13.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-14.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-15.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-16.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-17.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-18.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-19.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-20.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-21.jpg" />
    <img src="https://s3-us-west-2.amazonaws.com/s.cdpn.io/106114/zoom-22.jpg" />
    <div class="label">Linear easing</div>
</div>

<link href='//fonts.googleapis.com/css?family=Signika+Negative:300,400' rel='stylesheet' type='text/css'>
```

```
body {
  margin: 0;
  padding: 0;
  background-color: black;
}
#container {
  display: flex;
  min-height: 100vh;
}
#expo, #linear {
  flex-grow: 1;
  overflow: hidden;
  position: relative;
  color: white;
  font-size: 3em;
}
#linear {
  border-left: 2px solid black;
}
#expo {
  /*display: none;*/
}
img {
  visibility: hidden;
  position: absolute;
  top: 50%;
  left: 50%;
  min-width: 100%;
  min-height: 100%;
}
.label {
  position: relative;
  top: 0px;
  padding:10px;
  text-align: center;
  font-family: "Signika Negative", sans-serif;
  background-color: rgba(0,0,0,0.4);
}
```

```
//Get all the details on ExpoScaleEase here: https://greensock.com/docs/v3/Eases/ExpoScaleEase
gsap.set("img", {yPercent:-50, xPercent:-50, top:"50%", left:"50%", minWidth:"100%", position:"absolute"});

zoom({
  elements:"#expo img",
  repeat:-1,
  fade:0.7,
  duration:20, 
  direction:"in",
  useExpoEase:true
})
  //.pause();

zoom({
  elements:"#linear img",
  repeat:-1,
  fade:0,
  //to better see what's happening (flipping between images), uncomment the next two lines...
  //startScale:0.25,
  //endScale:0.5,
  duration:20, 
  direction:"in",
  useExpoEase:false
});


function zoom(config) {
  var elements = gsap.utils.toArray(config.elements),
      tl = gsap.timeline({repeat:config.repeat || 0}),
      duration = 1,
      fade = Math.min(0.99, (typeof(config.fade) === "number") ? config.fade : 0.5) * duration,
      startScale = config.startScale || 1,
      endScale = config.endScale || 2,
      scaleDifference = endScale - startScale,
      extendedScale = endScale + scaleDifference * 2,
      templateEase = config.ease || "none",
      useExpoEase = (config.useExpoEase !== false),
      ease = useExpoEase ? `expoScale(${startScale}, ${endScale}, ${templateEase})` : "none",
      extendedEase = useExpoEase ? ExpoScaleEase.config(endScale, extendedScale, templateEase) : gsap.parseEase("none"),
      partialScale = endScale + extendedEase(fade / duration) * (extendedScale - endScale),
      partialEase = useExpoEase ? `expoScale(${endScale}, ${partialScale}, ${templateEase})` : "none",
      i;
  tl.set(elements, {scale:startScale}, "-=" + fade);
  for (i = 0; i < elements.length; i++) {
    if (i) {
      tl.to(elements[i-1], {duration: fade, scale:partialScale, ease:partialEase}).set(elements[i-1], {visibility:"hidden"});
    }
    tl.to(elements[i], {duration: fade, autoAlpha:1}, "-=" + fade)
      .to(elements[i], {duration: duration, scale:endScale, ease:ease}, "-=" + fade);
  }
  if (config.direction === "out") {
    tl = tl.pause().tweenFromTo(tl.duration(), 0, {repeat:config.repeat});
  }
  if (config.duration) {
    tl.duration(config.duration);
  }
  return tl.play(0);
}


//for a simpler example that only shows a single image, 
//see https://codepen.io/GreenSock/pen/6239c068e182bdb8ff18926f519f8565


/*
//this is the plain vanilla version that hasn't been paramaterized and wrapped into a convenient (but more complex) zoom() function:

var images = document.querySelectorAll("#expo img"),
    tl = gsap.timeline({repeat:-1}),
    fade = 0.5,
    duration = 1,
    ease = "expoScale(1, 2)",
    partialScale = 2 + ExpoScaleEase.config(2, 4).getRatio(fade / duration) * 2,
    partialEase = "expoScale(2, partialScale)",
    i, ease;

for (i = 0; i < images.length; i++) {
  if (i) {
    tl.to(images[i-1], {duration: fade, scale:partialScale, ease:partialEase}).set(images[i-1], {visibility:"hidden"});
  }
  tl.to(images[i], { duration: fade, autoAlpha: 1 }, "-=" + fade)
    .to(images[i], { duration: duration, scale: 2, ease: ease }, "-=" + fade);
}
*/
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
