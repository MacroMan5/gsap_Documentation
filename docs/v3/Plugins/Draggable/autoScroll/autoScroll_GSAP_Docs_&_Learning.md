# autoScroll | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/autoScroll](https://gsap.com/docs/v3/Plugins/Draggable/autoScroll)  
**Last Updated:** 2025-05-23T00:28:39.707Z  
**Extracted:** 2025-05-31 16:56:03

---

# autoScroll | GSAP | Docs & Learning

```
<h1>Draggable autoScroll</h1>
<p>As of version 0.12.0, Draggable has auto-scrolling capabilities! Add <code>autoScroll:1</code> to the config object for normal-speed scrolling, or <code>autoScroll:2</code> would be twice as fast, etc. When your mouse moves within 40px of the edge of a scrollable container, it will start scrolling. The closer you get to the edge, the faster it will scroll. Try it out below...</p>
<div class="wrapper">
  <div id="container">
    <div class="box green" id="box">Drag me</div>
  </div>
</div>
<div class="controls">
  <ul>
    <li class="controlsTitle">Options</li>
    <li>
      <label><input type="checkbox" name="snap" id="snap" value="1" /> Snap end position to grid</label>
    </li>
    <li>
      <label><input type="checkbox" name="liveSnap" id="liveSnap" value="1" /> Live snap</label>
    </li>
  </ul>
</div>
```

```
body {
  padding: 1rem;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  flex-direction: column;
}

.wrapper {
  width: 60vw;
  height: 1020px;
  overflow: scroll;
}

#container {
  height: 801px;
  overflow: visible;
  padding: 0;
  position: relative;
}

.box {
  text-align: center;
  font-size: 18px;
  width: 196px;
  line-height: 100px;
  color: black;
  position: absolute;
  top: 0;
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  border-radius: 10px;
}

p {
  max-width: 70ch;
}

.controls {
  background-color: #222;
  border: 1px solid #555;
  color: #bbb;
  font-size: 18px;
  margin: 20px 0;
}
.controls ul {
  list-style: none;
  padding: 0;
  margin: 0;
}
.controls li {
  display: inline-block;
  padding: 8px 0 8px 10px;
  margin: 0;
}
.controls input {
  vertical-align: middle;
  cursor: pointer;
}
.controls .controlsTitle {
  border-right: 1px solid #555;
  border-bottom: none;
  padding-right: 10px;
}
```

```
// See https://greensock.com/gsap-1-16 for details.

const snapCheckbox = document.getElementById("snap");
const liveSnapCheckbox = document.getElementById("liveSnap");
const container = document.getElementById("container");

const gridWidth = 74;
const gridHeight = 50;
const gridRows = 28;
const gridColumns = 40;

// Create the grid cells
for (let i = 0; i < gridRows * gridColumns; i++) {
  const y = Math.floor(i / gridColumns) * gridHeight;
  const x = (i * gridWidth) % (gridColumns * gridWidth);

  const cell = document.createElement("div");
  cell.style.position = "absolute";
  cell.style.border = "1px solid #454545";
  cell.style.width = `${gridWidth - 1}px`;
  cell.style.height = `${gridHeight - 1}px`;
  cell.style.top = `${y}px`;
  cell.style.left = `${x}px`;

  container.prepend(cell);
}

// Set container and box sizes
gsap.set(container, {
  height: gridRows * gridHeight + 1,
  width: gridColumns * gridWidth + 1
});
gsap.set("#box", { width: 150, height: 100, lineHeight: "100px" });

function update() {
  const snap = snapCheckbox.checked;
  const liveSnap = liveSnapCheckbox.checked;

  Draggable.create("#box", {
    bounds: container,
    autoScroll: 1,
    edgeResistance: 0.65,
    type: "x,y",
    throwProps: true,
    liveSnap: liveSnap,

    onRelease: function () {
      this.tween.progress(1);
      const wrapper = document.querySelector(".wrapper");
      const tBounds = this.target.getBoundingClientRect();
      const wBounds = wrapper.getBoundingClientRect();
      let wCenter = wBounds.left + wBounds.width / 2;
      let tCenter = tBounds.left + tBounds.width / 2;
      const scroll = {};

      if (tBounds.right > wBounds.right || tBounds.left < wBounds.left) {
        scroll.x = wrapper.scrollLeft + (tCenter - wCenter);
      }

      if (tBounds.bottom > wBounds.bottom || tBounds.top < wBounds.top) {
        wCenter = wBounds.top + wBounds.height / 2;
        tCenter = tBounds.top + tBounds.height / 2;
        scroll.y = wrapper.scrollTop + (tCenter - wCenter);
      }

      gsap.to(wrapper, this.tween.duration(), { scrollTo: scroll });
      this.tween.progress(0);
    },

    snap: {
      x: function (endValue) {
        return snap || liveSnap
          ? Math.round(endValue / gridWidth) * gridWidth
          : endValue;
      },
      y: function (endValue) {
        return snap || liveSnap
          ? Math.round(endValue / gridHeight) * gridHeight
          : endValue;
      }
    }
  });
}

function applySnap() {
  if (snapCheckbox.checked || liveSnapCheckbox.checked) {
    document.querySelectorAll(".box").forEach((element) => {
      const transform =
        element._gsTransform || gsap.getProperty(element, "x,y");
      gsap.to(element, 0.5, {
        x: Math.round(transform.x / gridWidth) * gridWidth,
        y: Math.round(transform.y / gridHeight) * gridHeight,
        delay: 0.1,
        ease: Power2.easeInOut
      });
    });
  }
  update();
}

// Hook up event listeners
snapCheckbox.addEventListener("change", applySnap);
liveSnapCheckbox.addEventListener("change", applySnap);

// Initial setup
update();
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
