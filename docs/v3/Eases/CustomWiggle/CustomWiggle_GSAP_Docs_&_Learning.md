# CustomWiggle | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Eases/CustomWiggle](https://gsap.com/docs/v3/Eases/CustomWiggle)  
**Last Updated:** 2025-05-23T00:14:09.108Z  
**Extracted:** 2025-05-31 16:56:03

---

# CustomWiggle | GSAP | Docs & Learning

```
<link href='https://fonts.googleapis.com/css?family=Signika+Negative:300,400,700' rel='stylesheet' type='text/css'>
<h1>CustomWiggle built-in types</h1>

<div class="group">
  <div class="box" id="easeOut"><svg viewBox="0 0 250 150"><path id="easeOutSVG"></path></svg>"easeOut"</div>
  <div class="ball" id="easeOutBall"></div>
</div>

<div class="group">
  <div class="box" id="easeInOut"><svg viewBox="0 0 250 150"><path id="easeInOutSVG"></path></svg>"easeInOut"</div>
  <div class="ball" id="easeInOutBall"></div>
</div>

<div class="group">
  <div class="box" id="anticipate"><svg viewBox="0 0 250 150"><path id="anticipateSVG"></path></svg>"anticipate"</div>
  <div class="ball" id="anticipateBall"></div>
</div>

<div class="group">
  <div class="box" id="uniform"><svg viewBox="0 0 250 150"><path id="uniformSVG"></path></svg>"uniform"</div>
  <div class="ball" id="uniformBall"></div>
</div>

<div class="group">
  <div class="box" id="random"><svg viewBox="0 0 250 150"><path id="randomSVG"></path></svg>"random"</div>
  <div class="ball" id="randomBall"></div>
</div>

<p>Click on any box to trigger that animation.</p>
```

```
body {
  margin:0;
  padding:0;
  overflow:hidden;
  background-color: #0e100f;
  font-family: Signika Negative, Asap, sans-serif;
  color: #ccc;
  font-weight: 300;
  font-size: 1em;
  line-height: 1em;
  padding: 20px;
  text-align: center;
}
svg {
  
  position:absolute;
  top: 0;
  left: 0;
  z-index: -1;
}
.ball {
  width: 40px;
  height: 40px; 
  margin: 50px 0 30px 0;
  border-radius: 50%;
  background-color: #ff8709;
  display: inline-block;
}
.group {
  
  display: inline-block;
  text-align: center;
  position: relative;
  margin-right: 0px;
  margin-top: 20px;
  cursor: pointer;
}
path {
  stroke-width: 3px;
  stroke: white;
  fill: none;
  opacity: 0.7;
}
.box {
  width: 150px;
  height:90px;
  background-color: #0ae448;
  color: black;
  text-align: center;
  font-weight: 400;
  font-size: 1.5em;
  line-height: 90px;
  position: relative;
  transform: translate3d(0,0,0);
  user-select: none;
  -webkit-user-select: none;
}
h1, strong {
  color: white;
  font-weight: 400;
}
a:link, a:visited {
  color:#90E500;
  text-decoration: none;
}
a:hover {
  text-decoration: underline;
}
```

```
gsap.registerPlugin(CustomEase, CustomWiggle);

var wiggles = 10; //tweak this to whatever number you want. 

//create the custom eases..
CustomWiggle.create("Wiggle.easeOut", {wiggles:wiggles, type:"easeOut"});
CustomWiggle.create("Wiggle.easeInOut", {wiggles:wiggles, type:"easeInOut"});
CustomWiggle.create("Wiggle.anticipate", {wiggles:wiggles, type:"anticipate"});
CustomWiggle.create("Wiggle.uniform", {wiggles:wiggles, type:"uniform"});
CustomWiggle.create("Wiggle.random", {wiggles:wiggles, type:"random"});


//now set up a master timeline that repeats 50 times...
var tl = gsap.timeline({repeat:50, repeatDelay:1, delay:1});
tl.add(wiggle("easeOut", 2))
  .add(wiggle("easeInOut", 2), "+=0.5")
  .add(wiggle("anticipate", 3), "+=0.5")
  .add(wiggle("uniform", 2), "+=0.5")
  .add(wiggle("random", 6), "+=0.5");


//for convenience, let the user click any of the boxes to trigger animation (which should pause the main timeline)
setupClick("easeOut", 2);
setupClick("easeInOut", 2);
setupClick("anticipate", 3);
setupClick("uniform", 2);
setupClick("random", 6);

//just a helper function for wiggling the box and ball for a particular ID, like "easeOut"
function wiggle(id, duration) {
  var tl = gsap.timeline();
  tl.to("#" + id, {duration:duration, rotation:30, ease:"Wiggle." + id})
    .to("#" + id + "Ball", {duration:duration, x:100, ease:"Wiggle." + id}, 0);
  return tl;
}

//a helper function for setting up the click behavior for each box according to ID 
function setupClick(id, duration) {
  var animation = wiggle(id, duration).pause();
    document.querySelector("#" + id).addEventListener("click", function() {
      tl.pause(0);
      animation.play(0);
    });
}

//NOTE: if you want to start in the opposite direction, just set invert:true in the CustomWiggle.create() vars. 

//graph them
CustomEase.getSVGData("Wiggle.easeOut", {width:248, height:73, x:1, y:2, path:"#easeOutSVG"});
CustomEase.getSVGData("Wiggle.easeInOut", {width:248, height:73, x:1, y:2, path:"#easeInOutSVG"});
CustomEase.getSVGData("Wiggle.anticipate", {width:248, height:73, x:1, y:2, path:"#anticipateSVG"});
CustomEase.getSVGData("Wiggle.uniform", {width:248, height:73, x:1, y:2, path:"#uniformSVG"});
CustomEase.getSVGData("Wiggle.random", {width:248, height:73, x:1, y:2, path:"#randomSVG"});
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
