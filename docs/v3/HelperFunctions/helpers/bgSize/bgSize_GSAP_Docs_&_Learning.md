# bgSize | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/bgSize](https://gsap.com/docs/v3/HelperFunctions/helpers/bgSize)  
**Last Updated:** 2025-05-23T00:19:44.809Z  
**Extracted:** 2025-05-31 16:56:03

---

# bgSize | GSAP | Docs & Learning

I was asked about animating to or from a `backgroundSize` of `"cover"` or `"contain"` with GSAP. ﻿**The problem:** GSAP interpolates between numbers, but how is it supposed to interpolate between something like "300px 250px" and "contain" (not a number)? So I whipped together a function that basically translates "contain" or "cover" into their px-based equivalents for that particular element at whatever size it is then. Once we've got it converted, it's easy t﻿o animate.

```
/*config is optional and can have any of the following properties:- size [string] - the size to set and convert into px before it gets returned, like "cover" or "150% auto".- nativeWidth [number] - native width of the image (in pixels)- nativeHeight [number] - native height of the image (in pixels)Simple example:// returns current backgroundSize in pxbgSize(".class");Advanced example:// sets the backgroundSize to "cover" and returns it in the equivalent px-based amount assuming the image's native width is 600px and height is 400px.bgSize(".class", {size: "cover", nativeWidth: 600, nativeHeight: 400});Note: if you can define the nativeWidth and nativeHeight, it helps becaues it can skip tasks like creatingan Image and loading the URL to detect the native size automatically. Sometimes images don't load fast enough,so skipping that step avoids the whole issue.*/function bgSize(element, config) {  config = config || {};  let e = gsap.utils.toArray(element)[0],    cs = window.getComputedStyle(e),    imageUrl = cs.backgroundImage,    { nativeWidth, nativeHeight } = config,    size = config.size || cs.backgroundSize,    image,    w,    h,    ew,    eh,    ratio;  if (imageUrl && (!/\d/g.test(size) || size.indexOf("%") > -1)) {    if (!nativeWidth || !nativeHeight) {      image = new Image();      image.setAttribute(        "src",        imageUrl.replace(/(^url\("|^url\('|^url\(|"\)$|'\)$|\)$)/gi, "")      );      nativeWidth = image.naturalWidth;      nativeHeight = image.naturalHeight;    }    ew = e.offsetWidth;    eh = e.offsetHeight;    if (!nativeWidth || !nativeHeight) {      console.log("bgSize() failed;", imageUrl, "hasn't loaded yet.");      nativeWidth = ew;      nativeHeight = eh;    }    ratio = nativeWidth / nativeHeight;    if (size === "cover" || size === "contain") {      if ((size === "cover") === nativeWidth / ew > nativeHeight / eh) {        h = eh;        w = eh * ratio;      } else {        w = ew;        h = ew / ratio;      }    } else {      // "auto" or %      size = size.split(" ");      size.push("");      w = ~size[0].indexOf("%")        ? (ew * parseFloat(size[0])) / 100        : nativeWidth;      h = ~size[1].indexOf("%")        ? (eh * parseFloat(size[1])) / 100        : nativeHeight;    }    size = Math.ceil(w) + "px " + Math.ceil(h) + "px";    config.size && (e.style.backgroundSize = size);  }  return size;}
```

For even more flexibility, you can use this unofficial plugin for animating the backgroundSize to/from "cover" or "contain" and it'll even let you apply a scale to the value. Plus if you animate to "cover" or "contain", it will actually set it to that value (instead of the pixel-based equivalent) so that it's responsive after the tween:

#### loading...

  CodePen Embed - BackgroundSizePlugin  

```
<h1>Click image to animate from "scaled-up" cover</h1>
<div class="photo"></div>
```

```
body, html {
  width:100%;
  height:100%;
  overflow:hidden;
}

body {
  display:flex;
  align-items:center;
  justify-content:center;
  flex-direction:column;
}

h1 {
  font-size:20px;
  text-align:center;
}
.photo {
  border:1px solid #999;
  width:80vw;
  height:80vh;
  background:url(https://assets.codepen.io/32887/circle-bg.gif);
  background-size:cover;
  background-position:center center;
  background-repeat:no-repeat;
  background-color:black;
}
```

```
// plugin
const BackgroundSizePlugin = {
  name: "backgroundSize",
  getSize(target, config) {
    let o = {};
    BackgroundSizePlugin.init.call(o, gsap.utils.toArray(target)[0], config);
    return {width: o.sw + o.cw, height: o.sh + o.ch};
  },
  init(target, vars) {
    typeof(vars) !== "object" && (vars = {size: vars});
    let cs = window.getComputedStyle(target),
      imageUrl = cs.backgroundImage,
      {nativeWidth, nativeHeight, scale, size} = vars,
      parsedScale = scale || scale === 0 ? scale : 1,
      data = this,
      image, w, h, ew, eh, ratio, start, end,
      getSize = (size, scale) => {
        if (!/\d/g.test(size) || size.indexOf("%") > -1) {
          ratio = nativeWidth / nativeHeight;
          if (size === "cover" || size === "contain") {
            if ((size === "cover") === (nativeWidth / ew > nativeHeight / eh)) {
              h = eh;
              w = eh * ratio;
            } else {
              w = ew;
              h = ew / ratio;
            }
          } else { // "auto" or %
            size = size.split(" ");
            size.push("");
            w = ~size[0].indexOf("%") ? ew * parseFloat(size[0]) / 100 : nativeWidth;
            h = ~size[1].indexOf("%") ? eh * parseFloat(size[1]) / 100 : nativeHeight;
          }
        } else {
          size = size.split(" ");
          size.push(nativeHeight);
          w = parseFloat(size[0]) || nativeWidth;
          h = parseFloat(size[1]);
        }
        return {w: Math.ceil(w * scale), h: Math.ceil(h * scale)};
      };
    if (imageUrl) {
      if (!nativeWidth || !nativeHeight) {
        image = new Image();
        image.setAttribute("src", imageUrl.replace(/(^url\("|^url\('|^url\(|"\)$|'\)$|\)$)/gi, ""));
        nativeWidth = image.naturalWidth;
        nativeHeight = image.naturalHeight;
      }
      ew = target.offsetWidth;
      eh = target.offsetHeight;
      if (!nativeWidth || !nativeHeight) {
        console.log("bgSize() failed;", imageUrl, "hasn't loaded yet.");
        nativeWidth = ew;
        nativeHeight = eh;
      }
      size || (size = cs.backgroundSize);
      start = getSize(cs.backgroundSize, 1);
      end = getSize(size, parsedScale);
      data.size = parsedScale === 1 ? size : end.w + "px " + end.h + "px";
      data.style = target.style;
      data.sw = start.w;
      data.cw = end.w - start.w;
      data.sh = start.h;
      data.ch = end.h - start.h;
    }
  },
  render(ratio, data) {
    data.style.backgroundSize = ratio === 1 ? data.size : (data.sw + data.cw * ratio).toFixed(1) + "px " + (data.sh + data.ch * ratio).toFixed(1) + "px";
  }
};
gsap.registerPlugin(BackgroundSizePlugin);


// now let's animate...
let tween = gsap.fromTo(".photo", {
  backgroundSize: {
    size: "cover",
    scale: 3, // optionally scale it!
    nativeWidth: 1200, // you don't have to define nativeWidth/nativeHeight but it makes calculations faster and more reliable because it can skip creating an Image and loading the URL.
    nativeHeight: 1200
  }
}, {
  backgroundSize: {
    size: "cover",
    nativeWidth: 1200, 
    nativeHeight: 1200
  }, 
  duration: 2
});

document.body.addEventListener("click", ()=> tween.restart());

// or you can grab the numeric width/height (in pixels) like this (returns an object like {width: 100, height: 100})
let containSize = BackgroundSizePlugin.getSize(".photo", {size: "contain", nativeWidth: 1200, nativeHeight: 1200}); 
console.log("containSize:", containSize);
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
