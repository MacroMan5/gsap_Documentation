# getScrollLookup | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/getScrollLookup](https://gsap.com/docs/v3/HelperFunctions/helpers/getScrollLookup)  
**Last Updated:** 2025-05-23T00:20:22.126Z  
**Extracted:** 2025-05-31 16:56:03

---

# getScrollLookup | GSAP | Docs & Learning

```


<div id="main-content">
  <div class="horizontal-container">
    <div class="section" id="section1">Section 1</div>
    <div class="section" id="section2">Section 2</div>
    <div class="section" id="section3">Section 3</div>
    <div class="section" id="section4">Section 4</div>
    <div class="section" id="section5">Section 5</div>
  </div>
</div>
<div class="navigation">
  <ul>
    <li><a href="#section1">Section 1</a></li>
    <li><a href="#section2">Section 2</a> (150vw)</li>
    <li><a href="#section3">Section 3</a></li>
    <li><a href="#section4">Section 4</a></li>
    <li><a href="#section5">Section 5</a></li>
  </ul>
</div>
```

```

body { 
  font-weight: 300;
  margin: 0;
}

.navigation {
  position: fixed;
  top: 0;
  left: 0;
}

.horizontal-container {
  width: 550vw;
  height: 100vh;
  max-height: 100%; 
  display: flex;
  flex-wrap: nowrap;
}

.section {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
  height: 100vh;
  border-right: 1px solid var(--color-surface-white);
}

#section2 {
  width: 150vw;
}

a {
  color: #0ae448
}

.navigation ul li {
  list-style: none;
  text-decoration: none;
  padding: 0;
  margin: 0;
}

.navigation ul {
  display: flex;
  gap: 1rem;
}
```

```
let container = document.querySelector(".horizontal-container")
let scrollContainer = document.querySelector("#main-content");
let sections = gsap.utils.toArray(".section");
let maxWidth = 0;

const getMaxWidth = () => {
  maxWidth = 0;
  sections.forEach((section) => {
    maxWidth += section.offsetWidth;
  });
};
getMaxWidth();
ScrollTrigger.addEventListener("refreshInit", getMaxWidth);

// GSAP create horizontal scroll
let horizontalScroll = gsap.to(sections, {
  x: () => `-${maxWidth - window.innerWidth}`,
  ease: 'none',
  scrollTrigger: {
    trigger: scrollContainer,
    pin: true,
    scrub: true,
    end: () => `+=${maxWidth}`,
    invalidateOnRefresh: true,
  }
});

let getPosition = getScrollLookup(".section", {start: "center center", containerAnimation: horizontalScroll});

gsap.utils.toArray(".navigation li a").forEach(el => {
  el.addEventListener("click", e => {
    e.preventDefault();
    gsap.to(window, {
      scrollTo: getPosition(el.getAttribute("href")),
      overwrite: "auto",
      duration: 1
    });
  });
});

/*
Returns a FUNCTION that you can feed an element to get its scroll position.
- targets: selector text, element, or Array of elements 
- config: an object with any of the following optional properties: 
    - start: defaults to "top top" but can be anything like "center center", "100px 80%", etc. Same format as "start" and "end" ScrollTrigger values.
    - containerAnimation: the horizontal scrolling tween/timeline. Must have an ease of "none"/"linear".
    - pinnedContainer: if you're pinning a container of the element(s), you must define it so that ScrollTrigger can make the proper accommodations.

You can call .add() on the returned function to add more targets with different config values, so they all use the same lookup like: 

let lookup = getScrollLookup(".targets", {});
lookup.add(".other-targets", {containerAnimation: tween})
lookup.add(".more-targets", {pinnedContainer: ".container", containerAnimation: tween2});
*/
function getScrollLookup(targets, {start, pinnedContainer, containerAnimation}) {
  targets = gsap.utils.toArray(targets);
  let initted,
      triggers = targets.map((el, i) => ScrollTrigger.create({
        trigger: el,
        start: start || "top top",
        pinnedContainer: pinnedContainer,
        refreshPriority: -10,
        onRefresh(self) {
          if (initted && Math.abs(self.start) > 999999) {
            triggers[i].kill();
            triggers[i] = ScrollTrigger.create({
              trigger: el,
              start: start || "start start",
              pinnedContainer: pinnedContainer,
              refreshPriority: -10,
            });
          }
        },
        containerAnimation: containerAnimation
      })),
      st = containerAnimation && containerAnimation.scrollTrigger,
      lookups = [],
      lookup = target => {
        let t = gsap.utils.toArray(target)[0],
            i = targets.indexOf(t);
        if (i < 0) {
          for (i = 0; i < lookups.length; i++) {
            if (lookups[i].targets.indexOf(t) !== -1) {
              return lookups[i](t);
            }
          }
          return console.warn("target not found", target);
        }
        return triggers[i].vars.containerAnimation ? st.start + (triggers[i].start / containerAnimation.duration()) * (st.end - st.start) : triggers[i].start;
      };
  lookup.targets = targets;
  lookup.add = (targets, config) => {
    lookups.push(getScrollLookup(targets, config));
    return lookup;
  };
  initted = true;
  return lookup;
}

/* old, simpler version that doesn't accommodate .add() functionality: */
// function getScrollLookup(targets, {start, pinnedContainer, containerAnimation}) {
//   let triggers = gsap.utils.toArray(targets).map(el => ScrollTrigger.create({
//         trigger: el,
//         start: start || "top top",
//         pinnedContainer: pinnedContainer,
//         refreshPriority: -10,
//         containerAnimation: containerAnimation
//       })),
//       st = containerAnimation && containerAnimation.scrollTrigger;
//   return target => {
//     let t = gsap.utils.toArray(target)[0],
//         i = triggers.length;
//     while (i-- && triggers[i].trigger !== t) {};
//     if (i < 0) {
//       return console.warn("target not found", target);
//     } 
//     return containerAnimation ? st.start + (triggers[i].start / containerAnimation.duration()) * (st.end - st.start) : triggers[i].start;
//   };
// }
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
