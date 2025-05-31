# fromTo | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/fromTo()](https://gsap.com/docs/v3/GSAP/Timeline/fromTo())  
**Last Updated:** 2025-05-23T00:23:21.416Z  
**Extracted:** 2025-05-31 16:56:03

---

# fromTo | GSAP | Docs & Learning

### fromTo( target:\[ Object | Array | String \], fromVars:Object, toVars:Object, position:\[ Number | String \] ) : self

Adds a `.fromTo()` tween to the end of the timeline - this is a convenience method that accomplishes exactly the same thing as `add( gsap.fromTo(...) )` but with less code.

#### Parameters

*   #### **target**: \[ Object | Array | String \]
    
    Target object (or array of objects) whose properties should be affected. This can also be CSS selector text like "#feature" or "h2.author" (GSAP will pass selector strings to `document.querySelectorAll()`).
    
*   #### **fromVars**: Object
    
    An object defining the starting values for each property that should be animated. Do **NOT** put special properties like duration, ease, delay, etc. here - those go in the **toVars** parameter.
    
*   #### **toVars**: Object
    
    An object defining the end values for each property that should be animated as well as any special properties like `duration`, `onComplete`, `ease`, etc.
    
*   #### **position**: \[ Number | String \]
    
    (default = `"+=0"`) - controls the insertion point in the timeline (by default, it's the end of the timeline). See options below, or the [Position Parameter article](https://gsap.com/resources/position-parameter) which has interactive timeline visualizations and a video. If you define a label that doesn't exist yet, it will **automatically be added to the end of the timeline**
    

### Returns : self[​](#returns--self "Direct link to Returns : self")

self (makes chaining easier)

### Details[​](#details "Direct link to Details")

Adds a [`gsap.fromTo()`](https://gsap.com/docs/v3/GSAP/gsap.fromTo\(\)) tween to the end of the timeline (or elsewhere using the "position" parameter) - this is a convenience method that accomplishes exactly the same thing as `add( gsap.fromTo(...) )` but with less code. For example:

```
var tl = gsap.timeline();var tween = gsap.fromTo(element, { x: -100 }, { duration: 1, x: 100 });tl.add(tween);//this line produces the same result as the previous two lines (just shorter)tl.fromTo(element, { x: -100 }, { duration: 1, x: 100 });
```

* * *

**See the [gsap.fromTo() docs](https://gsap.com/docs/v3/GSAP/gsap.fromTo\(\)) for all the details and special properties available for a `fromTo()` Tween.**

* * *

You can chain these calls together and use other convenience methods like [`to()`](https://gsap.com/docs/v3/GSAP/Timeline/to\(\)), [`call()`](https://gsap.com/docs/v3/GSAP/Timeline/call\(\)), [`set()`](https://gsap.com/docs/v3/GSAP/Timeline/set\(\)), etc. to build out sequences very quickly:

```
//create a timeline that calls myFunction() when it completesvar tl = gsap.timeline({ onComplete: myFunction });//now we'll use chaining, but break each step onto a different line for readability...//tween element's x from -100 to 100tl.fromTo(element, { x: -100 }, { duration: 1, x: 100 })  //then tween element's y to 50  .to(element, { duration: 1, y: 50 })  //then set element's opacity to 0.5 immediately  .set(element, { opacity: 0 })  //then call otherFunction()  .call(otherFunction)  //finally tween the rotation of all elements with the class "myClass" to 45 and stagger the start times by 0.25 seconds  .to(".myClass", { duration: 1.5, rotation: 45, stagger: 0.25 });
```

## Positioning animations in a timeline[​](#positioning-animations-in-a-timeline "Direct link to Positioning animations in a timeline")

By default, animations are added to the **end** of the timeline so that they're sequenced one-after-the-other but you can use the [position parameter](https://gsap.com/resources/position-parameter) to control precisely where things are placed. It typically comes after the **vars** parameter and it uses a flexible syntax with the following options:

*   **Absolute time** (in seconds) measured from the start of the timeline, as a **number** like `3`
    
    ```
    // insert exactly 3 seconds from the start of the timelinetl.fromTo(".class", { x: 100 }, { x: 200 }, 3);
    ```
    
*   **Label**, like `"someLabel"`. _If the label doesn't exist, it'll be added to the end of the timeline._
    
    ```
    // insert at the "someLabel" labeltl.fromTo(".class", { x: 100 }, { x: 200 }, "someLabel");
    ```
    
*   `"<"` The **start** of previous animation\*\*. _Think of `<` as a pointer back to the start of the previous animation._
    
    ```
    // insert at the START of the  previous animationtl.fromTo(".class", { x: 100 }, { x: 200 }, "<");
    ```
    
*   `">"` - The **end** of the previous animation\*\*. _Think of `>` as a pointer to the end of the previous animation._
    
    ```
    // insert at the END of the previous animationtl.fromTo(".class", { x: 100 }, { x: 200 }, ">");
    ```
    
*   A complex string where `"+="` and `"-="` prefixes indicate **relative** values. _When a number follows `"<"` or `">"`, it is interpreted as relative so `"<2"` is the same as `"<+=2"`._ Examples:
    
    *   `"+=1"` - 1 second past the end of the timeline (creates a gap)
    *   `"-=1"` - 1 second before the end of the timeline (overlaps)
    *   `"myLabel+=2"` - 2 seconds past the label `"myLabel"`
    *   `"<+=3"` - 3 seconds past the start of the previous animation
    *   `"<3"` - same as `"<+=3"` (see above) (`"+="` is implied when following `"<"` or `">"`)
    *   `">-0.5"` - 0.5 seconds before the end of the previous animation. It's like saying _"the end of the previous animation plus -0.5"_
*   A complex string based on a **percentage**. When immediately following a `"+="` or `"-="` prefix, the percentage is based on [total duration](https://gsap.com/docs/v3/GSAP/Tween/totalDuration\(\)) of the **animation being inserted**. When immediately following `"<"` or `">"`, it's based on the [total duration](https://gsap.com/docs/v3/GSAP/Tween/totalDuration\(\)) of the **previous animation**. _Note: total duration includes repeats/yoyos_. Examples:
    
    *   `"-=25%"` - overlap with the end of the timeline by 25% of the inserting animation's total duration
    *   `"+=50%"` - beyond the end of the timeline by 50% of the inserting animation's total duration, creating a gap
    *   `"<25%"` - 25% into the previous animation (from its start). Same as `">-75%"` which is negative 75% from the **end** of the previous animation.
    *   `"<+=25%"` - 25% of the inserting animation's total duration past the start of the previous animation. Different than `"<25%"` whose percentage is based on the **previous animation's** total duration whereas anything immediately following `"+="` or `"-="` is based on the **inserting animation's** total duration.
    *   `"myLabel+=30%"` - 30% of the inserting animation's total duration past the label `"myLabel"`.

\*Percentage-based values were added in GSAP 3.7.0  
\*\*The "previous animation" refers to the most recently-inserted animation, not necessarily the animation that is closest to the end of the timeline.

### Position Parameter Interactive Demo[​](#position-parameter-interactive-demo "Direct link to Position Parameter Interactive Demo")

#### loading...

  CodePen Embed - Position Parameter explainer - constructor  

```
<div id="app">
  <section class="boxes">
    <div ref="purple" class="item purple gradient-purple" data-color="#9d95ff" data-class="purple"></div>
     <div ref="green" class="item green gradient-green" data-color="#0ae448" data-class="green"></div>
  </section>

  <div class="interface">    
      <button class="button" :class="{ playing : paused }" @click="togglePlayback">
        <svg aria-hidden="true" class="button__svg" fill="#fff" xmlns="http://www.w3.org/2000/svg" id="Layer_1" data-name="Layer 1" viewBox="0 0 24 24">
          <g class="pause">
            <path d="M10,17a1,1,0,0,1-1-1V8a1,1,0,0,1,2,0v8A1,1,0,0,1,10,17Z" />
            <path d="M14,17a1,1,0,0,1-1-1V8a1,1,0,0,1,2,0v8A1,1,0,0,1,14,17Z" />
          </g>
          <path class="play" d="M16.57,11.32,10.31,7.15a.8.8,0,0,0-1.25.68v8.34a.81.81,0,0,0,1.25.68l6.26-4.17A.81.81,0,0,0,16.57,11.32Z" />
        </svg>
        <span class="button__text">pause</span>
      </button>
    
    <div class="timeline" ref="timeline">
      <div class="timeline__item" v-for="(item,index) in timelineItems" :style="item.style" :class="item.class" :key="item.class">
        <span></span>
      </div>
    </div>
    <div class="times">
      <div v-for="(ms,index) in roundedMilliseconds" :class="{ label: index === labelPosition * 10 }" :key="index">
        <span>{{ index / 10 }}</span>    
      </div>
    </div>
    <div class="scrubber" ref="scrubber"></div>
  </div>
  
  <div class="code-container">
    <span class="code">tl.to(".green-box", { x: {{ endX }}, duration: 1 }<span :class="{ 'hide-comma' : hidePosition }">,&nbsp;</span></span>
    <span class="code position-text" :class="hidePosition ? 'hide-position' : ''">{{ formattedPosition }}</span>
    <span class="code">);</span>
  </div>
  
  <div class="code-container mobile">
    <div>tl.to(".green-box", {</div>
    <div>&nbsp;&nbsp;x: {{ endX }},</div>
    <div>&nbsp;&nbsp;duration: 1</div>
    <div>}<span :class="hidePosition ? 'hide-comma' : ''">,&nbsp;</span><span class="position-text" :class="{ 'hide-position' : hidePosition }">{{ formattedPosition }}</span>);</div>
  </div>
  
  <div class="options">
    
    <div class="options__container flow reference">
      <h3>Reference Point</h3>

        <label class="radio radio--simple">
          <input :class="{ 'checked': 'timelineStart' === referencePoint }" type="radio" value="timelineStart" v-model="referencePoint"><span class="box"></span><span class="info">Start of timeline</span>
        </label>
 
      

        <label class="radio radio--simple">
          <input :class="{ 'checked': 'timelineEnd' === referencePoint }" type="radio" value="timelineEnd" v-model="referencePoint"><span class="box"></span><span class="info">End of timeline</span>
        </label>



        <label class="radio">
          <input :class="{ 'checked': 'previousStart' === referencePoint }" type="radio" value="previousStart" v-model="referencePoint"><span class="box">&lt;</span><span class="info">Start of <span class="purpleTxt">previous animation</span></span>
        </label>

      

        <label class="radio">
          <input :class="{ 'checked': 'previousEnd' === referencePoint }" type="radio" value="previousEnd" v-model="referencePoint"> <span class="box">&gt;</span><span class="info">End of <span class="purpleTxt">previous animation</span></span>
        </label>

      

        <label class="radio">
          <input v-bind:class="{ 'checked': 'label' === referencePoint }" type="radio" value="label" v-model="referencePoint"> <span class="box box--label">myLabel</span><span class="info">Label</span>
        </label>
   
    </div>
    
    <div class="options__container offsets">
      <h3>Offset</h3>
      
      <div class="offset" :class="{ 'offset--previous': useRecent && usePrevious }">
      <input class="number" @wheel="" v-model="offsetNumber" type="number" :min="-range" :max="range" :step="offsetType === 'percent' ? 5 : 0.5">
      <label class="offset__type" :class="{ 'checked': 'seconds' === offsetType }">
        <input type="radio" value="seconds" v-model="offsetType"> Seconds
      </label>
      <label v-if="referencePoint !== 'timelineStart'" class="offset__type" :class="{ 'checked': 'percent' === offsetType }">
        <input type="radio" value="percent" v-model="offsetType" :disabled="referencePoint === 'timelineStart'"> Percent
      </label>  
      </div>
      <div v-if="usePrevious">
        <label class="radio radio--simple">
          <input type="checkbox" :class="{ 'checked': useRecent }"  v-model="useRecent"><span class="box"></span><span class="info">Use percentage of <span class="purpleTxt"> previous animation</span></span>
        </label>
      </div>
    </div>
    
  </div>
</div>
```

```

$mobile: 640px;

:root {
  --number-size: 1rem;
}

.item {
  width: 45px;
  height: 45px;
  border-radius: 10px;
  margin-top: 0.5rem
}

.gradient-green {
  background: var(--gradient-macha),
  url('https://assets.codepen.io/16327/noise-e82662fe.png'); /* Replace with the path to your noise texture image */
      background-blend-mode: color-dodge; /* Blend the noise texture with the gradient */
}

.gradient-purple {
  background: var(--gradient-purple-haze),
  url('https://assets.codepen.io/16327/noise.png'); /* Replace with the path to your noise texture image */
      background-blend-mode: color-dodge; /* Blend the noise texture with the gradient */
}

body {
  padding: 0.5rem;
  min-height: 100vh;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  letter-spacing: 1px;
  margin: 0;
}

h3 {
  margin-bottom: 0.5rem;
  color: #fffce1;
  font-weight: 400;
  font-size: 1rem;
}

#app {
  opacity: 0;
}

.flow > * + * {
  margin-top: 0.5rem;
}

.interface {
  // opacity:0;
  position: relative;
  padding: 2.2rem 2rem 2.2rem;
  background-color: #262626;
  border-radius: 10px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
  width: clamp(300px, 80vw, 900px);

  &__title {
    position: relative;
    color: #fffce1;
    display: block;
    width: 100%;
    padding-bottom: 1rem;
    padding-left: 3px;
    display: flex;
    flex-direction: row;
    h1 {
      font-size: 1.2rem;
    }
  }
}

.timeline > * + * {
  margin-top: 0.5rem;
}

.timeline__item {
  width: 2px;
  margin: 0.5rem;
  border-radius: 999px;
  box-sizing: border-box;
  text-align: center;
  height: 18px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.timeline__item.purple span {
  display: none;
  font-size: 0.85rem
}

.scrubber {
  position: absolute;
  bottom: 2rem;
  left: 0;
  width: 20px;
  height: 20px;
  border-radius: 99px;
  background-color:#fffce1;
  z-index: 1;
}

.button__svg {
  width: 2rem;
  height: 2rem;
  margin-top: 0px;
  pointer-events: none;
}

.button {
  position: absolute;
  font-size: 0;
  border: none;
  outline: none;
  background-color: transparent;
  top: 10px;
  left: 1rem;
  cursor: pointer;
  display: block;
  padding: 0;
}

.button.playing {
  .pause {
    opacity: 1;
  }
  .play {
    opacity: 0;
  }
}

.button:not(.playing) {
  .pause {
    opacity: 0;
  }
  .play {
    opacity: 1;
  }
}

.times {
  width: calc(100% - 20px);
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  z-index: 999;
  margin-left: 10px;
}

.times > * {
  position: relative;
}

.times div {
  margin-top: 1rem;
  width: 0.5px;
  height: 5px;
  background-color: #fffce1;
  opacity: 0.7;
  position: relative;
}

.times span {
  display: none;
  font-size: var(--number-size);
}

.times div:nth-child(5n + 1) {
  height: 10px;
  background-color: #fffce1;
  opacity: 1;
}

.times div:nth-child(5n + 1) span {
  display: block;
  color: #fffce1;
  text-align: center;
  position: absolute;
  width: auto;
  height: 1rem;
  top: 1rem;
  left: 50%;
  transform: translateX(-50%);
  z-index:2;
}

.times .label {
  height: 10px;
  background-color: #befd92;
}

.times .label span {
  position: absolute;
  width: 1rem;
  height: 1rem;
  top: 1rem;
  left: 0%;
  transform: translateX(-0.5rem);
  z-index:2;
}

.times .label:after {
  content: '';
  font-size: 0.85rem;
  text-align: center;
  position: absolute;
  background-size: 70%;
  background-position: center bottom;
  background-repeat: no-repeat;
  width: 60px;
  height: 30px;
  left: -30px;
  top: 400%;
  z-index: 9;
  background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' id='Capa_1' x='0' y='0' version='1.1' viewBox='0 0 344.406 344.406' xml:space='preserve'%3E%3Cpath fill='%232191FB' d='M243.243 0h-142.08c-13.767.044-24.916 11.193-24.96 24.96v298.8c0 21 21.04 31.2 37.48 5l58.52-93.28 58.52 93.28c16.44 26.2 37.48 15.96 37.48-5V24.96C268.159 11.193 257.01.044 243.243 0z'/%3E%3C/svg%3E");
}

.boxes {
  display: flex;
  margin-bottom: 0.5rem;
  z-index: -1;
  pointer-events: none;
  flex-direction: column;
}

.emoji {
  margin: 1rem;
  width: 2rem;
  height: 2rem;
}

.heart {
  width: 3rem;
  height: 2.5rem;
  object-position: 85%;
}

#options {
  margin-top: 2.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  
  .input {
    margin-top: 2rem;
    font-size: 1.3rem;
    border: none;
    outline: none;
    padding: 1rem 0.5rem;
    border-bottom: solid 4px #51da85;
  }
}

.radios {
  display: flex;
}

.radio {
  display: flex;
  align-items: center;
}

.radio .box {
  width: 50px;
  background-color: #464646;
  border-radius: 5px;
  cursor: pointer;
  padding: 0.5rem;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 0.75rem;
}

.radio .info {
  display: inline-block;
  margin-left:1rem;
}


.radio:nth-of-type(5) .checked ~ .box {
  border-color: #2191FB;
  background-color: #2191FB;
  color: #fff;
}

.checked ~ .box {
  border-color: #9d95ff;
  background-color: #9d95ff;
  color: #fffce1;
}

.radio input {
  position: absolute;
  opacity: 0;
}

.radio--simple .box {
  position: relative;
  width: 15px;
  height: 15px;
  padding: 0;
  border-radius: 99%;
  border-color: #ddd;
}

.radio--simple .box:after {
  position: absolute;
  content: '';
  width: 75%;
  height: 75%;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 99%;
  opacity: 0;
  background-color: #464646; 
}

.radio--simple .checked ~ .box {
  border-color: #51da85;
  background-color: #51da85;
}
.radio--simple .checked ~ .box:after {
  opacity: 1;
}


.offset {
  background-color: #464646;
  border-radius: 5px;
  cursor: pointer;
  display: flex;
  font-size: 1rem;
  display: inline-flex;
  overflow: hidden;
  
  input:not(.number) {
    opacity: 0;
    position: absolute;
  }
  
  .offset__type {
    flex-grow: 1;
    display: flex;
    align-items: center;
    padding: 0.25rem;
    font-size: 0.8rem;
  }
  
  .offset__type.checked {
    background-color: #0ae448;
    color: #1b1b1b;
  }
}

.offsets .radio--simple {
  margin-top: 1rem;
}

.offsets .radio--simple .checked ~ .box {
  background-color: #9d95ff;
}

.offset--previous {
  .offset__type.checked {
    background-color: #9d95ff;
  }
}

.offset--previous {
  border-color: #9d95ff;
}

.text {
  width: 100%;
}
.label {
  display: block;
  margin-top: 1rem;
}

.number {
  border: none;
  padding: 0.5rem 1rem;
  padding-right: 0.2rem;
  font-size: 1rem;
  border-radius: 20px;
  outline: none;
  background-color: #464646;
  color: #fff
}


.helperText {
  opacity: 0;
  min-height: 135px;
  text-align: center;
}

.greenTxt {
  color: #25b961;
  font-weight: bold;
}
.purpleTxt {
  color: #9d95ff;
  font-weight: bold;
}
.blueTxt {
  color: #2191FB;
  font-weight: bold;  
}

.invalid {
  height: 2rem;
  font-size: 0.85rem;
}

footer {
  display: flex;
}

.code {
  opacity: 0.6;
}

.position-text {
  opacity: 1;
  margin-bottom: 0.2em;
  padding-bottom: 0;
  font-weight: 600;
}

.code-container {
  font-family: "Fira Code", monospace;
  font-size: 0.9rem;
  padding:0.51rem;
  align-items: center;
  line-height: 2em;
  border-radius: 10px;
  padding-top: 2rem;
  border-top-left-radius: 0;
  border-top-right-radius: 0;
  background-color: #262626;
}

.code-container:not(.mobile) {
  display: flex;
  justify-content: center;
  white-space: pre;
}

.code-container.mobile {
  display: none;
}

.position-text {
  color: #fffce1
}

.code {
  white-space: pre;
}

.options {
  display: flex;
  flex-wrap: wrap;
  flex: 1 1 auto;
  padding-top: 2rem;
}

.options__container {
  flex: 0 0 50%;
  max-width: 50%;
}

.hide-comma {
  display: none;
}

.code-container .position-text.hide-position {
  margin-left: 0;
  display: none;
}

@media (max-width: $mobile) {
  
  .options__container {
    flex: 0 0 100%;
    max-width: 100%;
    padding-top: 1.5rem;
  }
  
  .code-container:not(.mobile) {
    display: none;
  }

  .code-container.mobile {
    display: block;
    padding-left: 2rem;
    padding-bottom: 1rem;
  }
}

















```

[View Compiled](#0)

```
console.clear();

// "<25%" (use recent), "<+=25%" (use inserting)

gsap.registerPlugin(Draggable, CustomEase, CustomWiggle);

CustomWiggle.create("wiggle", {wiggles:5, type:"easeInOut"});

new Vue({
  el: "#app",
  data() {
    return {
      labelPosition: 1,
      paused: false,
      roundedMilliseconds: 0,
      percentRange: 200,
      secondsRange: 5,
      useRecent: false,
      referencePoint: "timelineStart",
      offsetType: "seconds",
      offsetNumber: 1,
      position: 0,
      hidePosition: false,
      lastSecond: 1,
      lastPercent: 50,
      endX: 500,
      timelineItems: [],
      timelineData: [
        { class: "purple gradient-purple" }, 
        { class: "green gradient-green" }
      ]
    }
  },
  mounted() {
    
    this.setScrubber = gsap.quickSetter(this.$refs.scrubber, "x", "px");
    this.clampSeconds = gsap.utils.clamp(-this.secondsRange, this.secondsRange);
    this.clampPercent = gsap.utils.clamp(-this.percentRange, this.percentRange);
    this.mapSize = gsap.utils.mapRange(30, 90, 1.1, 0.65);
        
    this.timeline = gsap.timeline();    
       
    this.createScrubber();
    this.renderTimeline();
    
    window.addEventListener("resize", this.onResize);
    
    this.$nextTick(() => {
      this.onResize();
      this.timeline.eventCallback("onUpdate", this.updateScrubber);
      gsap.to("#app", { opacity: 1 });
    });    
  },
  computed: {
    formattedPosition() {
      if (this.hidePosition) {
        return "";
      }
      if (this.referencePoint !== "timelineStart") {
        return `"${this.position}"`;
      }
      return this.position;
    },
    range() {
      return this.offsetType === "percent" ? this.percentRange : this.secondsRange;
    },
    usePrevious() {
      return this.referencePoint.includes("previous") && this.offsetType === "percent";
    }
  },
  watch: {
    formattedPosition: "animatePosition",
    useRecent: "renderTimeline",
    referencePoint(value) {      
      if (value === "timelineStart") {
        this.offsetType = "seconds";
      }
      
      this.renderTimeline();
    },
    offsetNumber(value) {      
      value = parseFloat(value);      
      if (isNaN(value)) return;      
            
      if (this.offsetType === "percent") {
        this.offsetNumber = this.clampPercent(value);
      } else {
        this.offsetNumber = this.clampSeconds(value);
      }
      
      this.renderTimeline();
    },
    offsetType(value) {
      
      if (value === "percent") {
        this.lastSecond = this.offsetNumber;
        this.offsetNumber = this.lastPercent;
      } else {
        this.lastPercent = this.offsetNumber;
        this.offsetNumber = this.lastSecond;
      }
      
      this.renderTimeline();
    }
  },
  methods: {  
    renderTimeline() {
            
      this.position = this.getPosition();
      this.endX = this.scrubber.maxX - 56;
      
      let tl = this.timeline;
      
      tl.progress(0)
        .clear(true)            
        .addLabel("myLabel", this.labelPosition)      
        .to(this.$refs.purple, {
          ease: "none",
          duration: 2,
          x: this.endX,
          data: this.timelineData[0]
        }, 0)
        .to(this.$refs.green, {
          ease: "none",
          duration: 1,
          x: this.endX,
          data: this.timelineData[1]
        }, this.position);
      
      let timelineItems = [];
      let time = tl.duration();
      let children = tl.getChildren();
      let milliseconds = time * 10;
      this.roundedMilliseconds = Math.floor(milliseconds) + 1; 
      
      let fontSize = this.mapSize(this.roundedMilliseconds);
      document.documentElement.style.setProperty('--number-size', fontSize + "rem");

      children.forEach((child, index) => {
        let duration = child.totalDuration();
        let startTime = child.startTime();
        let width = (duration / time) * 100;
        let startPosition = (startTime / time) * 100;
             
        timelineItems[index] = {
          ...child.data,
          style: {
            width: `${width}%`,
            marginLeft: `${startPosition}%`
          }
        };
      });
      
      // trigger render
      this.timelineItems = timelineItems;
    },
    getPosition() {
      
      this.hidePosition = false;
      let value = parseFloat(this.offsetNumber);
            
      let isNegative = value < 0;      
      let isPercent = this.offsetType === "percent";
      
      if (this.referencePoint !== "timelineStart") {
        value = Math.abs(value);
      }
      
      let isZero = value === 0;
      let offset = isPercent ? `${value}%` : value;
      
      switch(this.referencePoint) {
        case "timelineStart": return value;
        
        case "timelineEnd": 
          if (isZero) {
            this.hidePosition = true;
            return "";
          }
          return (isNegative ? "-=" : "+=") + offset;
        
        case "previousStart":
          if (isZero) {
            return "<"; 
          }          
          if (isPercent && !this.useRecent) {
            return (isNegative ? "<-=" : "<+=") + offset;
          }
          return (isNegative ? "<-" : "<") + offset;
        
        case "previousEnd":
          if (isZero) {
            return ">"; 
          }
          if (isPercent && !this.useRecent) {
            return (isNegative ? ">-=" : ">+=") + offset;
          }
          return (isNegative ? ">-" : ">") + offset;
        
        case "label": 
          if (isZero) return "myLabel";
          return "myLabel" + (isNegative ? "-=" : "+=") + offset;
        
        default: return 0;
      }
    },
    createScrubber() {
            
      this.scrubber = new Draggable(this.$refs.scrubber, {
        type: "x",
        cursor: "pointer",
        bounds: this.$refs.timeline,
        zIndexBoost: false,
        onPress: () => {
          this.timeline.pause();
          this.paused = true;
        },
        onDrag: () => {
          let progress = this.normalize(this.scrubber.x);
          this.timeline.progress(progress);
        }
      });
    },    
    togglePlayback() {
      if (this.timeline.progress() > 0.98) {
        this.paused = false;
        return this.timeline.restart();
      }
      this.paused = !this.paused;
      this.timeline.paused(this.paused);
    },        
    onResize() {
      this.scrubber.update(true);
      this.normalize = gsap.utils.normalize(this.scrubber.minX, this.scrubber.maxX);
      this.interpolate = gsap.utils.interpolate(this.scrubber.minX, this.scrubber.maxX);
      this.updateScrubber();
      this.renderTimeline();
    },    
    updateScrubber() {
      let x = this.interpolate(this.timeline.progress());
      this.setScrubber(x);
    }
  }
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

### External CSS

1.  [https://codepen.io/GreenSock/pen/wvZQKQP.css](https://codepen.io/GreenSock/pen/wvZQKQP.css)

### External JavaScript

1.  [https://assets.codepen.io/16327/gsap-latest-beta.min.js](https://assets.codepen.io/16327/gsap-latest-beta.min.js)
2.  [https://unpkg.com/gsap@3/dist/Draggable.min.js](https://unpkg.com/gsap@3/dist/Draggable.min.js)
3.  [https://unpkg.com/vue@2.6.14/dist/vue.js](https://unpkg.com/vue@2.6.14/dist/vue.js)
4.  [https://cdnjs.cloudflare.com/ajax/libs/prism/1.23.0/prism.min.js](https://cdnjs.cloudflare.com/ajax/libs/prism/1.23.0/prism.min.js)
5.  [https://assets.codepen.io/16327/CustomWiggle3.min.js](https://assets.codepen.io/16327/CustomWiggle3.min.js)
6.  [https://assets.codepen.io/16327/CustomEase3.min.js](https://assets.codepen.io/16327/CustomEase3.min.js)

Be sure to read the [Position Parameter article](https://gsap.com/resources/position-parameter) which includes interactive timeline visualizations and a video.

info

By default, `immediateRender` is `true` in `fromTo()` tweens, meaning that they immediately render their starting state regardless of any delay that is specified. You can override this behavior by passing `immediateRender: false` in the vars parameter so that it will wait to render until the tween actually begins.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
