# anchorsToProgress | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/anchorsToProgress](https://gsap.com/docs/v3/HelperFunctions/helpers/anchorsToProgress)  
**Last Updated:** 2025-05-23T00:19:45.622Z  
**Extracted:** 2025-05-31 16:56:03

---

# anchorsToProgress | GSAP | Docs & Learning

```
<h1>anchorsToProgress() GSAP Demo</h1>

<svg id="svg" viewBox="0 0 900 200">
  
</svg>
<div class="nav">
  
  <button class="previous">previous</button>
  <button class="next">next</button>
</div>
```

```
h1 {
  margin: 20px;
  text-align: center;
}

svg {
  overflow: visible;
  height: 100%;
  max-width: 100%;
}

circle {
  fill: #fffce1;
}

path {
  stroke-width: 3px;
  stroke: #444;
  fill: none;
}

.nav {
  display: flex;
  justify-content: center;
  padding: 0 0 20px 0;
  align-content: center;
  gap: 1rem;
}

```

[View Compiled](#0)

```
gsap.registerPlugin(MotionPathPlugin, DrawSVGPlugin);

let anchors = [{x:50, y:130}, {x:300, y:10}, {x:500, y:70}, {x:700, y:190}, {x:850, y:100}], // anchor coordinates (feel free to change these if you want)
    rawPath = MotionPathPlugin.arrayToRawPath(anchors, {curviness:0.5}),
    path = buildPath(anchors, rawPath), // builds all the anchors and paths, returns the red SVG path
    progressArray = anchorsToProgress(rawPath), // calculate the progress value associated with each anchor, returned as an array.
    curIndex = 0,
    drawPath = gsap.from(path, { // this is the tween of the red path. We pause it initially and animate its progress.
      ease: "none",
      drawSVG: false,
      paused: true,
      duration: 5
    });

// This function calculates the progress value along the rawPath for each anchor and returns an array accordingly.
// So if the rawPath has 5 anchors, the array that's returned will have 5 progress values, each between 0 and 1.
function anchorsToProgress(rawPath, resolution) {
  resolution = ~~resolution || 12;
  if (!Array.isArray(rawPath)) {
    rawPath = MotionPathPlugin.getRawPath(rawPath);
  }
  MotionPathPlugin.cacheRawPathMeasurements(rawPath, resolution);
  let progress = [0],
    length, s, i, e, segment, samples;
  for (s = 0; s < rawPath.length; s++) {
    segment = rawPath[s];
    samples = segment.samples;
    e = segment.length - 6;
    for (i = 0; i < e; i+=6) {
      length = samples[(i / 6 + 1) * resolution - 1];
      progress.push(length / rawPath.totalLength);
    }
  }
  return progress;
}

// jump to a specific anchor (animate the tween to that progress value)
function goToAnchor(index) {
  curIndex = index;
  gsap.to(drawPath, {
    progress: progressArray[curIndex],
    overwrite: true,
    duration: 2
  });
}

// click as many times and as quickly as you want.
document.querySelector(".next").addEventListener("click", function() {
  if (curIndex < anchors.length - 1) {
    goToAnchor(curIndex + 1);
  }
});
document.querySelector(".previous").addEventListener("click", function() {
  if (curIndex > 0) {
    goToAnchor(curIndex - 1);
  }
});


// -- setup ---
function buildPath(anchors, rawPath) {
  let svg = document.querySelector("#svg"),
      pathTemplate = createSVG("path", svg, {d: MotionPathPlugin.rawPathToString(rawPath)}),
      path = createSVG("path", svg, {d: MotionPathPlugin.rawPathToString(rawPath)}),
      i;
  gsap.set(path, {stroke: "#0ae448", strokeWidth: 5});
  for (i = 0; i < anchors.length; i++) {
    createSVG("circle", svg, {cx: anchors[i].x, cy: anchors[i].y, r: 5});
  }
  return path;
}

function createSVG (type, container, attributes) {
    var element = document.createElementNS("http://www.w3.org/2000/svg", type),
        reg = /([a-z])([A-Z])/g,
        p;
    for (p in attributes) {
        element.setAttributeNS(null, p.replace(reg, "$1-$2").toLowerCase(), attributes[p]);
    }
    if (typeof(container) === "string") {
        container = document.querySelector(container);
    }
    container.appendChild(element);
    return element;
}

goToAnchor(1);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
