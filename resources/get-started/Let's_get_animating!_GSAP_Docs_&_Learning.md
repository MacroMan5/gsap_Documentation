# Let's get animating! | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/resources/get-started/](https://gsap.com/resources/get-started/)  
**Last Updated:** 2025-05-24T13:15:19.710Z  
**Extracted:** 2025-05-31 16:56:03

---

# Let's get animating! | GSAP

Welcome! In this article **we're going to cover GSAP's core fundamentals and animate some HTML elements**. 🥳

If that's not your end goal, don't worry. Whatever you plan to animate, whichever framework you use - the techniques and principles covered here will serve you well.

What is "GSAP"?

The GreenSock Animation Platform (GSAP) is an industry-celebrated suite of tools used on over 11 million sites, including a ton of [award‑winning](https://www.awwwards.com/websites/gsap-animation) ones! You can use GSAP to **animate pretty much** **_anything JavaScript can touch, in any framework._** Whether you want to animate UI, SVG, Three.js or React components - [GSAP has you covered](https://gsap.com/blog/why-gsap/).

**The core library** contains everything you need to create [blazing fast](https://gsap.com/js/speed.html), cross-browser friendly animations. This is what we'll be stepping through in this article.

In addition to the core, there are a variety of [plugins](https://gsap.com/docs/v3/Plugins/). **_You don't need to learn them in order to get started_**, but they can help with specific animation challenges like [scroll based animation](https://gsap.com/docs/v3/Plugins/ScrollTrigger), [draggable](https://gsap.com/docs/v3/Plugins/Draggable) interactions, [morphing](https://gsap.com/docs/v3/Plugins/MorphSVGPlugin), etc.

## Creating an animation.[​](#creating-an-animation "Direct link to Creating an animation.")

Let's start by animating an HTML element with a class of **_"box"_**.

```
gsap.to(".box", { x: 200 })
```

A single animation like this is called a **['tween'](https://gsap.com/docs/v3/GSAP/Tween)** This tween is saying "hey GSAP, animate the element with a class of '.box' to an x of 200px (like `transform: translateX(200px)`)".

#### loading...

  CodePen Embed - gsap.to()  

```
<div class="box green"></div>
```

```
/* Global styles come from external css https://codepen.io/GreenSock/pen/gOWxmWG */

body {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  min-height: 100vh;
  margin: 0;
  overflow: hidden;
}

.box {
  display: block;
}
```

```
gsap.to(".box", { 
  x: 200,
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

Let's take a closer look at the syntax.

![](https://gsap.com/assets/images/tween-diagram-39f72740ce8fddcca921341f8a4bd007.png)

We've got a **method**, a **target** and a **vars object** which all contain information about the animation

**The method(s)**

There are four types of tweens:

`gsap.to()` - This is the most common type of tween. A `.to()` tween will start at the element's current state and **animate "to" the values defined in the tween.**

`gsap.from()` - Like a backwards `.to()` where it **animates "from" the values defined in the tween** and ends at the element's current state.

`gsap.fromTo()` - **You define _both_ the starting _and_ ending values.**

`gsap.set()` **Immediately sets properties** (no animation). It's essentially a zero-duration `.to()` tween.

Let's look at them in action!

#### loading...

  CodePen Embed - gsap tweens  

```
<main>

  <form>
    <label>
      <input type="radio" id="to" name="method" value="to" checked>
      to</label>
    <label>
      <input type="radio" id="from" name="method" value="from">
      from</label>
    <label>
      <input type="radio" id="fromTo" name="method" value="fromTo">
      fromTo</label>
    <label>
      <input type="radio" id="set" name="method" value="set">
      set</label>
  </form>

  <svg viewBox="0 0 100 20">
    <circle class="outline from-outline" stroke="grey" fill="none" stroke-dasharray='1.2' stroke-width="0.3" cx="10" cy="10" r="9.7" />
    <circle class="outline center-outline" stroke="grey" fill="none" stroke-dasharray='1.2' stroke-width="0.3" cx="50" cy="10" r="9.7" />
    <circle class="outline to-outline" stroke="grey" fill="none" stroke-dasharray='1.2' stroke-width="0.3" cx="90" cy="10" r="9.7" />
    <circle class="circle" stroke-width="0.3" fill="#0ae448" cx="50" cy="10" r="10" />
  </svg>
<div class="code-container">
  
    <code class="code-to language-js">
      gsap.to(".circle", {
      x: 40,
      fill: 'blue',
      });
    </code>

    <code class="code-from language-js">
      gsap.from(".circle", {
      x: -40,
      fill: 'blue',
      });
    </code>

    <code class="code-fromTo language-js">
      gsap.fromTo( ".circle",{
      x: -40,
      fill: 'blue',
      },
      {
      x: 40,
      fill: 'green'
      });
    </code>
  
  <code class="code-set language-js">
      gsap.set(".circle", {
      x: 40,
      fill: 'blue',
      });
    </code>
  </div>
</main>
```

```
/* Global styles come from external css https://codepen.io/GreenSock/pen/gOWxmWG */

body {
  padding: 0;
  margin: 0;
  overflow: hidden;
}
main {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  min-height: 100vh;
  margin: 0;
  padding: 0;
  background-color: #0e100f;
}

.token.function {
  color: #93c763;
}

main > * + * {
  margin-top: 1rem;
}

.box {
  display: block;
}

form {
  display: flex;
  font-size: 1.3rem;
}

form > * + * {
  margin-left: 0.5rem;
}

svg {
  /*   height: 100vh; */
  max-width: 50vw;
  overflow: visible;
}

code {
  padding: 1rem !important;
}

.outline {
  visibility: hidden;
}

.code-container {
  min-height: 100px;
  display: flex;
  align-items: center;
  justify-content: center;
}

code {
  position: absolute;
}
```

```
let tl = gsap.timeline();
  gsap.set(".outline, code", { autoAlpha: 0 });
gsap.set(".code-to", {
        autoAlpha: 1
      })

var form = document.querySelector("form");
form.addEventListener("change", function () {
  let type = document.querySelector('input[name="method"]:checked').value;

  gsap.set(".circle", { clearProps: "all" });
  gsap.set(".outline, code", { autoAlpha: 0 });

  tl.clear();
  switch (type) {
    case "to":
      tl.set(".code-to", {
        autoAlpha: 1
      })
      .to(".to-outline", {
        autoAlpha: 1
      }).to(".circle", {
        duration: 1.1,
        ease: "none",
        x: 40,
        fill: "#00bae2"
      });
      break;
    case "set":
      tl.set(".code-set", {
        autoAlpha: 1
      }).set(".circle", {
        x: 40,
        fill: "#00bae2"
      }, "+=0.5");
      break;
    case "from":
      tl.set(".code-from", {
        autoAlpha: 1
      })
      .to(".from-outline", {
        autoAlpha: 1
      }).from(".circle", {
        duration: 1.1,
        ease: "none",
        x: -40,
        fill: "#00bae2"
      });
      break;
    case "fromTo":
      tl.set(".code-fromTo", {
        autoAlpha: 1
      })
        .to([".from-outline", ".to-outline"], {
          autoAlpha: 1,
          stagger: 0.25
        })
        .fromTo(
          ".circle",
          {
            x: -40,
            fill: "#00bae2"
          },
          {
            duration: 1.5,
            ease: "none",
            x: 40,
            fill: "#0ae448"
          }
        );
  }
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

**The target (or targets)**

Next up we have to tell GSAP what we want to animate. Under the hood GSAP uses `document.querySelectorAll()`, so for HTML or SVG targets we can use selector text like `".class"` and `"#id"`. Or you can pass in a variable or even an Array.

```
// use a class or IDgsap.to(".box", { x: 200 });// a complex CSS selectorgsap.to("section > .box", { x: 200 });// a variablelet box = document.querySelector(".box");gsap.to(box, { x: 200 })// or even an Array of elementslet square = document.querySelector(".square");let circle = document.querySelector(".circle");                                      gsap.to([square, circle], { x: 200 })
```

**The variables**

The vars object contains all the information about the animation. These can be arbitrary properties you want to animate, or **_special properties_** that influence the behavior of the animation - like `duration`, `onComplete` or `repeat`.

```
gsap.to(target, {  // this is the vars object  // it contains properties to animate  x: 200,  rotation: 360,  // and special properties  duration: 2})
```

## So what properties can I animate?[​](#so-what-properties-can-i-animate "Direct link to So what properties can I animate?")

GSAP can animate **almost anything**, there is no pre-determined list. This includes CSS properties, custom object properties, even CSS variables and complex strings! The most commonly animated properties are transforms and opacity.

tip

Transforms are a web animator's best friend. They can be used to move your elements around, scale them up and spin them around. Transforms and opacity are also very performant because they don't affect layout, so it's less work for the browser.

When possible, use transforms and opacity for animation rather than layout properties like "top", "left" or "margin". You'll get smoother animations!

## Transform shorthand[​](#transform-shorthand "Direct link to Transform shorthand")

You may be familiar with transforms from CSS:

```
transform: rotate(360deg) translateX(10px) translateY(50%);
```

GSAP provides a **shorthand** for transforms. The previous line of CSS would be written like so.

```
{ rotation: 360, x: 10, yPercent: 50 }
```

Here's a list of the shorthand transforms and some other commonly used properties.

| GSAP | Description or equivalent CSS |
| --- | --- |
| x: 100 | transform: translateX(100px) |
| y: 100 | transform: translateY(100px) |
| xPercent: 50 | transform: translateX(50%) |
| yPercent: 50 | transform: translateY(50%) |
| scale: 2 | transform: scale(2) |
| scaleX: 2 | transform: scaleX(2) |
| scaleY: 2 | transform: scaleY(2) |
| rotation: 90 | transform: rotate(90deg) |
| rotation: "1.25rad" | Using Radians - no CSS alternative |
| skew: 30 | transform: skew(30deg) |
| skewX: 30 | transform: skewX(30deg) |
| skewY: "1.23rad" | Using Radians - no CSS alternative |
| transformOrigin: "center 40%" | transform-origin: center 40% |
| opacity: 0 | adjust the elements opacity |
| autoAlpha: 0 | shorthand for opacity & visibility |
| duration: 1 | animation-duration: 1s |
| repeat: -1 | animation-iteration-count: infinite |
| repeat: 2 | animation-iteration-count: 2 |
| delay: 2 | animation-delay: 2 |
| yoyo: true | animation-direction: alternate |

The best way to learn is by experimenting. This demo below is a live code playground, go ahead and tweak the values to make the box move!

#### loading...

  CodePen Embed - gsap.to() - playground  

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

Units

By default GSAP will use px and degrees for transforms but you can use other units like, vw, radians or even do your own JS calculations or relative values!

```
x: 200, // use default of pxx: "+=200" // relative valuesx: '40vw', // or pass in a string with a different unit for GSAP to parsex: () => window.innerWidth / 2, // you can even use functional values to do a calculation!  rotation: 360 // use default of degreesrotation: "1.25rad" // use radians
```

## What else can I animate?[​](#what-else-can-i-animate "Direct link to What else can I animate?")

Pretty much **anything** - If you're not sure, give it a try! Can't figure it out? Pop over to the [forums](https://gsap.com/community/) and we'll give you a hand.

### CSS properties[​](#css-properties "Direct link to CSS properties")

Transforms, colors, padding, border radius, GSAP can animate it all! Just remember to camelCase the properties - e.g. `background-color` becomes `backgroundColor`.

#### loading...

  CodePen Embed - backgroundColor  

```
<div class="box green"></div>
```

```
/* Global styles come from external css https://codepen.io/GreenSock/pen/gOWxmWG */

body {
  display: flex;
  align-items: center;
  justify-content: space-around;
  min-height: 100vh;
  margin: 0;
  overflow: hidden;
}

.box {
  display: block;
}
```

```
gsap.to(".box", { 
  duration: 2,
  backgroundColor: '#8d3dae',
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

caution

Although GSAP **can** animate almost every CSS property, we recommend sticking to transforms and opacity when possible. Properties like filter and boxShadow are CPU-intensive for browsers to render. Animate with care and make sure to test on low-end devices.

### SVG attributes[​](#svg-attributes "Direct link to SVG attributes")

Just like HTML elements, SVG elements can be animated with transform shorthands. Additionally you can animate SVG attributes like `width`, `height`, `fill`, `stroke`, `cx`, `opacity` and even the SVG `viewBox` itself using an `attr` object.

#### loading...

  CodePen Embed - Animating SVG  

```
<svg id="svg" viewBox="0 0 100 100">
   <rect class="svgBox" fill="#28a92b" x="0" y="35" width="30" height="30" rx="2" />
</svg>
```

```
/* Global styles come from external css https://codepen.io/GreenSock/pen/gOWxmWG */

body {
  display: flex;
  align-items: center;
  justify-content: space-around;
  min-height: 100vh;
  margin: 0;
  overflow: hidden;
}

svg {
  height: 90vh;
  max-height: 300px;
  border: solid 2px white;
  overflow: visible;
}
```

```
gsap.to(".svgBox", { 
  duration: 2,
  x: 100, // use transform shorthand (this is now using SVG units not px, the SVG viewBox is 100 units wide)
  xPercent: -100,
  // or target SVG attributes
  attr: {
    fill: '#8d3dae',
    rx: 50, 
  },
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

### Any numeric value, color, or complex string containing numbers[​](#any-numeric-value-color-or-complex-string-containing-numbers "Direct link to Any numeric value, color, or complex string containing numbers")

When we say **anything** we mean **anything**. GSAP doesn't even need DOM elements in order to animate properties. You can target literally any property of any object, even arbitrary ones you create like this:

```
//create an objectlet obj = { myNum: 10, myColor: "red" };gsap.to(obj, {  myNum: 200,  myColor: "blue",  onUpdate: () => console.log(obj.myNum, obj.myColor)});
```

### Canvas[​](#canvas "Direct link to Canvas")

Advanced example

In the demo below we have a box drawn with HTML canvas. We're animating x and y values stored in a position object and then we update the canvas on each tick of the animation.

**_GSAP is often used this way to animate in Three.js, HTML canvas and Pixi.js:_**

#### loading...

  CodePen Embed - Animating Canvas  

```
<canvas id="canvas" width="300" height="300"></canvas>
```

```
/* Global styles come from external css https://codepen.io/GreenSock/pen/gOWxmWG */

body {
  display: flex;
  align-items: center;
  justify-content: space-around;
  min-height: 100vh;
  margin: 0;
  overflow: hidden;
}

#canvas {
  height: 80vh;
  max-height: 300px;
  overflow: visible;
  border: solid 2px white;
}
```

```
const canvas = document.getElementById("canvas");
const ctx = canvas.getContext("2d");
ctx.fillStyle = "#28a92b";

let position = { x: 0, y: 0 };

function draw() {
  // erase the canvas
  ctx.clearRect(0, 0, 300, 300);
  // redraw the square at it's new position
  ctx.fillRect(position.x, position.y, 100, 100);
}

//animate x and y of point
gsap.to(position, { 
  x: 200, 
  y: 200, 
  duration: 4,
  // unlike DOM elements, canvas needs to be redrawn and cleared on every tick
  onUpdate: draw 
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

## Special Properties[​](#special-properties "Direct link to Special Properties")

To adjust how a tween behaves we can pass in some special properties. In fact, we've looked at one already - `duration`.

special properties

You can check them all out in [our documentation](https://gsap.com/docs/v3/GSAP/Tween), but here are some of most common ones.

| Property | Description |
| --- | --- |
| duration | Duration of animation (seconds) Default: 0.5 |
| delay | Amount of delay before the animation should begin (seconds) |
| repeat | How many times the animation should repeat. |
| yoyo | If true, every other repeat the tween will run in the opposite direction. (like a yoyo) Default: false |
| stagger | Time (in seconds) between the start of each target's animation (if multiple targets are provided) |
| ease | Controls the rate of change during the animation, like the motion's "personality" or feel. Default: "power1.out" |
| onComplete | A function that runs when the animation completes |

Let's look at some of these in more detail...

## Repeats and alternating repeats[​](#repeats-and-alternating-repeats "Direct link to Repeats and alternating repeats")

`repeat` does exactly what you might think - it allows you to play an animation more than once. `repeat` is often paired with `yoyo` in order to reverse the direction each cycle. Change the code to `yoyo:false` in the demo below to see the difference.

#### loading...

  CodePen Embed - Special properties  

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

tip

Do you want your animation to repeat infinitely? No problem! Use `repeat: -1`

## Delays[​](#delays "Direct link to Delays")

You can `delay` the start of an animation by a certain number of seconds. You can also use `repeatDelay` to add a delay to the start of any repeat iterations.

#### loading...

  CodePen Embed - gsap.to() with a special properties  

```
<div class="box green"></div>
<div class="box purple"></div>
```

```
/* Global styles come from external css https://codepen.io/GreenSock/pen/gOWxmWG */

body {
  display: flex;
  align-items: center;
  justify-content: space-around;
  min-height: 100vh;
  margin: 0;
  overflow: hidden;
}

.box {
  display: block;
}
```

```
gsap.to(".green", { 
  rotation: 360,
  duration: 1,
  repeat: 1,
  repeatDelay: 1,
});


gsap.to(".purple", { 
  rotation: 360,
  duration: 1,
  delay: 1 // delay the start of this animation
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

So far so good. But... these animations aren't very exciting yet. **Easing** to the rescue!

---

*This documentation was extracted from the database for URLs containing 'gsap'*
