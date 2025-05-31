# gsap.registerEffect() | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/gsap.registerEffect()](https://gsap.com/docs/v3/GSAP/gsap.registerEffect())  
**Last Updated:** 2025-05-23T00:22:30.521Z  
**Extracted:** 2025-05-31 16:56:03

---

# gsap.registerEffect() | GSAP | Docs & Learning

Once an effect has been [registered](https://gsap.com/docs/v3/GSAP/gsap.registerEffect\(\)), you can access it directly on the `gsap.effects` object like this:

```
//assumes that an effect named "explode" has already been registeredgsap.effects.explode(".box", {  direction: "up", //can reference any properties that the author decides - in this case "direction"  duration: 3,});
```

Or, if you set `extendTimeline: true` on the effect when registering it, you'll even be able to call it DIRECTLY on timelines in order to have the results of the effect inserted into that timeline (see below). Effects make it easy for anyone to author custom animation code wrapped in a function (which accepts `targets` and a `config` object) and then associate it with a specific `name` so that it can be called anytime with new targets and configurations. For example, maybe we want to be able to make things fade (which is rather silly because it's so simplistic, but the goal here is to show how it could work):

```
// register the effect with GSAP:gsap.registerEffect({  name: "fade",  effect: (targets, config) => {    return gsap.to(targets, { duration: config.duration, opacity: 0 });  },  defaults: { duration: 2 }, //defaults get applied to any "config" object passed to the effect  extendTimeline: true, //now you can call the effect directly on any GSAP timeline to have the result immediately inserted in the position you define (default is sequenced at the end)});// now we can use it like this:gsap.effects.fade(".box");// or directly on timelines:let tl = gsap.timeline();tl.fade(".box", { duration: 3 })  .fade(".box2", { duration: 1 }, "+=2")  .to(".box3", { x: 100 });
```

#### loading...

  CodePen Embed - GSAP Effects Simple Demo  

```
<link href='https://fonts.googleapis.com/css?family=Signika' rel='stylesheet' type='text/css'>
  <div id="demo">
    <h2>GSAP Effects Simple Demo</h2>
    <div class="box green"></div>
    <div class="box purple"></div>
    <div class="box orange"></div>
    <div class="box green"></div>
    <div class="box purple"></div>
    <div class="box orange"></div>
    <div class="box green"></div>
    <div class="box purple"></div>
  </div>
```

```
body{display:flex;align-items:center;justify-content:center;min-height:100vh;}


h1 {
  font-size: 36px;
}

h2 {
  font-size: 30px;
  text-align: center;
}

h3 {
  font-size: 24px;
}

p {
  line-height: 22px;
  margin-bottom: 16px;
  width: 650px;
}

#demo {
  height: 100%;
  position: relative;
  display: inline-block;
}
.box {
  position: relative;
  border-radius: 6px;
  margin-top: 4px;
  display: inline-block;
}

```

```
gsap.registerEffect({
    name: "fade",
    defaults: {duration: 2}, //defaults get applied to the "config" object passed to the effect below
    effect: (targets, config) => {
        return gsap.to(targets, {duration: config.duration, opacity: 0});
    }
});

//now we can use it like this:
//gsap.effects.fade(".box");

document.querySelectorAll(".box").forEach(function(box) {
  box.addEventListener("mouseenter", function() {
    gsap.effects.fade(this);
  });
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

GSAP provides 4 key services here:

*   It parses the "targets" into an array. So if selector text is passed in, it becomes an array of elements passed to the effect function.
*   It applies defaults to the config object every time. No need to add a bunch of if statements or apply the defaults yourself.
*   It provides a centralized way of registering/accessing these "effects".
*   If you set `extendTimeline: true`, the effect's name will be added as a method to GSAP's Timeline prototype, meaning that you can insert an instance of that effect directly into any timeline like:

```
//with extendTimeline: truevar tl = gsap.timeline();tl.yourEffect(".class", { configProp: "value" }, "+=position");//without extendTimeline: true, you'd have to do this to add an instance to the timeline:tl.add(  gsap.effects.yourEffect(".class", { configProp: "value" }),  "+=position");
```

So it can save you a lot of typing if you're making heavy use of an effect in your sequences.

caution

**important**: any effect with `extendTimeline:true` **must** return a GSAP-compatible animation that could be inserted into a timeline (a Tween or Timeline instance)

Register Effects

GreenSock registerEffect() Tutorial - YouTube

For a quick overview of how to register effects, check out this video from the Snorkl.tv's [Creative Coding Club](https://www.creativecodingclub.com/bundles/creative-coding-club?ref=44f484) - one of the best ways to learn the basics of how to use GSAP.

Effects are also easily shared between different projects and people. To view effects that have already been created, check out [the CodePen collection](https://codepen.io/collection/bdffa09755cbd27a69b22771bd98e565/).

Here's an example of multiple pre-made fade effects being generated so that they can be reused later:

#### loading...

  CodePen Embed - Multiple pre-made effects  

```
<div class="box purple fadeSlideTo">to</div>
<div class="box green fadeSlideFrom">from</div>
<div class="box blue fadeSlideFromTo">fromTo</div>
```

```
body {
  display: flex;
  align-items: flex-start;
  justify-content: center;
  min-height: 100vh;
  flex-direction: column;
}
```

```
const gsapEffects = [
  { 
    id: "fadeSlideTo",  
    props: { opacity: 0.5, x: 300, yoyo: true, repeat: -1 }
  },
  { 
    id: "fadeSlideFrom", 
    animate: 'from',
    props: { opacity: 0.25, x: 300, yoyo: true, repeat: -1  }
  },
  { 
    id: "fadeSlideFromTo", 
    animate: 'fromTo', 
    props: { opacity: 0.1, x: 300}, 
    props2: { opacity: 1, x: 600, yoyo: true, repeat: -1  }
  }
];

gsapEffects.forEach(effect => {
  gsap.registerEffect({
    name: effect.id,
    defaults: { duration: 1 },
    extendTimeline: true,
    effect(targets, config) {
      if(effect.animate === 'from'){
        return gsap.from(targets, {...effect.props,...config })
      } 
      else if (effect.animate === 'fromTo'){ 
        return gsap.fromTo(targets, {...effect.props,...config }, {...effect.props2})
        }
      else {
        return gsap.to(targets, {...effect.props,...config })
      }
    }
  });
});



let tl = gsap.timeline();
tl.fadeSlideTo(".fadeSlideTo")
  .fadeSlideFrom(".fadeSlideFrom", 0)
  .fadeSlideFromTo(".fadeSlideFromTo", 0)
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

### External CSS

1.  [https://codepen.io/GreenSock/pen/xxmzBrw/fcaef74061bb7a76e5263dfc076c363e.css](https://codepen.io/GreenSock/pen/xxmzBrw/fcaef74061bb7a76e5263dfc076c363e.css)

### External JavaScript

1.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/gsap.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/gsap.min.js)
2.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/CSSRulePlugin.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/CSSRulePlugin.min.js)
3.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/CustomBounce3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/CustomBounce3.min.js)
4.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/CustomEase3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/CustomEase3.min.js)
5.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/CustomWiggle3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/CustomWiggle3.min.js)
6.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/DrawSVGPlugin3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/DrawSVGPlugin3.min.js)
7.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/Draggable.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/Draggable.min.js)
8.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/EaselPlugin.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/EaselPlugin.min.js)
9.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/EasePack.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/EasePack.min.js)
10.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/GSDevTools3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/GSDevTools3.min.js)
11.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/InertiaPlugin.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/InertiaPlugin.min.js)
12.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/MorphSVGPlugin3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/MorphSVGPlugin3.min.js)
13.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/MotionPathHelper.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/MotionPathHelper.min.js)
14.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/MotionPathPlugin.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/MotionPathPlugin.min.js)
15.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/Physics2DPlugin3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/Physics2DPlugin3.min.js)
16.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/PhysicsPropsPlugin3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/PhysicsPropsPlugin3.min.js)
17.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/PixiPlugin.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/PixiPlugin.min.js)
18.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/ScrambleTextPlugin3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/ScrambleTextPlugin3.min.js)
19.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/ScrollToPlugin.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/ScrollToPlugin.min.js)
20.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/ScrollTrigger.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/ScrollTrigger.min.js)
21.  [https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/SplitText3.min.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/SplitText3.min.js)
22.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/TextPlugin.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.5.1/TextPlugin.min.js)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
