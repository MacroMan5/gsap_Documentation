# gsap.matchMediaRefresh() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.matchMediaRefresh()](https://gsap.com/docs/v3/GSAP/gsap.matchMediaRefresh())  
**Last Updated:** 2025-05-23T00:22:13.322Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.matchMediaRefresh() | GSAP | Docs & Learning

```
<header class="center pad-l">
  <h1>gsap.matchMedia()</h1>
  <p class="lead">Use matchMedia and the prefers-reduced-motion media feature for easy, accessibility-friendly animation.</p>
  <div class="checkbox">
  <input type="checkbox" id="motionToggle" class="vh" name="motionToggle" value="false">
  <label for="motionToggle">Reduced animation please</label>
</div>
</header>


<section class="gray">
  <div class="box gradient-green"></div>
</section>

<section class="bottom">
  <p><strong>Pretty cool, right?</strong></p>
  <p>You can read more about reduced motion and vestibular disorders in this <a href="https://css-tricks.com/introduction-reduced-motion-media-query/">blog post</a> on CSS tricks</p>
  <p>How do I <a href="https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion#user_preferences">adjust my reduced motion setting?</a></p>
  <p>Check out <a href="https://greensock.com">GSAP</a> today. </p>
</section>
```

```
header {
  flex-direction: column;
}

.lead {
  padding: 0 20px;
  text-align: center;
}

.gray {
  width: 100%;
  height: 100vh;
}
.box {
  width: 150px;
  height: 150px;
  position: absolute;
  z-index: 0;
  left: 50%;
  top: 50%;
  transform: translate3d(-50%, -50%, 0);
}

.gray p {
  font-size: 1.4em;
  margin: 0;
  padding: 30px;
  line-height: 1.4em;
}

.bottom {
  width: 100%;
  text-align: center;
  padding: 150px 30px;
  font-size: 1.2em;
  box-sizing: border-box;
}
```

```
gsap.registerPlugin(ScrollTrigger);

let reduceMotionCB = document.querySelector("#motionToggle");
reduceMotionCB.checked = window.matchMedia("(prefers-reduced-motion: reduce)").matches;
reduceMotionCB.addEventListener("change", gsap.matchMediaRefresh); // force all matchMedia() stuff to revert and re-run

let breakPoint = 800;
let mm = gsap.matchMedia();

mm.add({
  isDesktop: `(min-width: ${breakPoint}px)`, // <- when ANY of these are true, the function below gets invoked
  isMobile: `(max-width: ${breakPoint - 1}px)`
}, (context) => {

  let {isDesktop, isMobile} = context.conditions;
  let reduceMotion = reduceMotionCB.checked; // if we weren't using a checkbox, we could just add another condition above: "(prefers-reduced-motion: reduce)"
  let tl = gsap.timeline({
    scrollTrigger: {
      trigger: ".gray",
      scrub: 1,
      end: "200%",
      pin: true
    }
  });
  tl.to(".box", { 
    scale: reduceMotion ? 1.1 : 2
  }).to(".box", { 
    scale: 1 
  });

  if (!reduceMotion) { // don't rotate the box if reduced motion was requested
    gsap.to(".box", {
      rotation: 360,
      ease: "none",
      duration: 5,
      repeat: -1
    });
  }

  gsap.set(".box", {
    innerText: isDesktop ? "Desktop" : "Mobile",

  });

  // optionally return a cleanup function
  return () => console.log("cleanup");
});

```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
