# Modifiers | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/CorePlugins/Modifiers](https://gsap.com/docs/v3/GSAP/CorePlugins/Modifiers)  
**Last Updated:** 2025-05-23T00:15:05.830Z  
**Extracted:** 2025-05-31 16:56:03

---

# Modifiers | GSAP | Docs & Learning

What are internal plugins?

ModifiersPlugin is an internal plugin, It is **automatically included in GSAP's core** and **doesn't have to be loaded using gsap.registerPlugin()**.

You can think of internal plugins as just a part of GSAP.

### Description[​](#description "Direct link to Description")

You can define a "modifier" function for almost any property. This modifier intercepts the value that GSAP would normally apply on each update ("tick"), feeds it to your function as the first parameter and lets you run custom logic, returning a new value that GSAP should then apply. This is perfect for tasks like snapping, clamping, wrapping, or other dynamic effects.

### value, target[​](#value-target "Direct link to value, target")

The modifier functions are passed two parameters:

1.  `value` (_number_ | _string_) - The about-to-be-applied value from the regular tween. This is often a number, but could be a string based on whatever the property requires. For example if you're animating the `x` property, it would be a number, but if you're animating the `left` property it could be something like `"212px"`, or for the `boxShadow` property it could be `"10px 5px 10px rgb(255,0,0)"`.
    
2.  target (_object_) - The target itself.
    

For example, change the `x` of one object based on the `y` of another object or change `rotation` based on the `direction` it is moving. Below are some examples that will help you get familiarized with the syntax.

### Snap rotation[​](#snap-rotation "Direct link to Snap rotation")

The tween below animates 360 degrees but the modifier function forces the value to jump to the closest 45-degree increment. Take note how the modifier function gets passed the value of the property that is being modified, in this case a `rotation` number.

#### loading...

  CodePen Embed - ModifiersPlugin: rotation snap  

```

<div class="wrapper">

  <div class="arrow"></div>


</div>
```

```
/* Global styles come from external css https://codepen.io/GreenSock/pen/JGaKdQ*/
body{display:flex;align-items:center;justify-content:center;min-height:100vh;}


.arrow {
  display:block;
  position:relative;
  width:150px;
  height:150px;
  background-size: contain;
  background-repeat: no-repeat;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 24 24' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M7.07615 16.6173C7.23093 16.2436 7.59557 16 8.00003 16H10.5V3C10.5 2.44772 10.9477 2 11.5 2H12.5C13.0523 2 13.5 2.44772 13.5 3V16H16C16.4045 16 16.7691 16.2436 16.9239 16.6173C17.0787 16.991 16.9931 17.4211 16.7071 17.7071L12.7071 21.7071C12.3166 22.0976 11.6834 22.0976 11.2929 21.7071L7.29292 17.7071C7.00692 17.4211 6.92137 16.991 7.07615 16.6173Z' fill='%230ae448'/%3E%3C/svg%3E");
}
```

```
var degrees = 45;
var tween = gsap.to(".arrow", {
  duration: 4,
  rotation: 360,
  modifiers: {
    rotation: gsap.utils.unitize(function(rotation) {
      //snap to 45 degree increments
      return Math.round(rotation / degrees) * degrees;   
    })
  },
 // in GSAP 3 you can do this instead:
 // snap: {rotation: degrees},
 ease: "none",
 repeat: 6,
})
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

If snapping is all that you're wanting to do, we recommend using the [SnapPlugin](https://gsap.com/docs/v3/GSAP/CorePlugins/Snap) that is built into GSAP's core.

### Clamp with Modulus[​](#clamp-with-modulus "Direct link to Clamp with Modulus")

The tween below animates `x` to 500 but the modifier function forces the value to wrap so that it's always between 0 and 100.

#### loading...

  CodePen Embed - ModifiersPlugin: Clamp using Modulus  

```

  <h3>tweened x value: <span id="tweenedX"</span></h3>
  <h3>modified x value: <span id="modifiedX"</span></h3>
  <div class="box green"></div>
```

```
/* Global styles come from external css https://codepen.io/GreenSock/pen/JGaKdQ*/

body{display:flex;align-items:center;justify-content:center;min-height:100vh;flex-direction: column; gap: 1rem}
h3 {
  color:#aaa;
  width: 100vw;
  text-align: left
}

h3 span {
  color:#fff;
}

.box {
  display:block;
  position:relative;
}
```

```
var tweenedX = document.getElementById("tweenedX"),
    modifiedX = document.getElementById("modifiedX")

gsap.to(".box", {
  duration: 5, 
  x: 500,
  modifiers: {
    x: function(x) {
      x = parseInt(x);
      tweenedX.textContent = x.toFixed(2);
      var newX = x % 100; 
      modifiedX.textContent = newX.toFixed(2) // value between 0 and 100
      return newX + 'px';
    }
  }, ease: "none"
})
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

Here's the same sort of technique but using GSAP's [wrap utility function](https://gsap.com/docs/v3/GSAP/UtilityMethods/wrap\(\)):

#### loading...

  CodePen Embed - GSAP 3 wrap() and wrapYoyo() utilities demo  

```
<h2>GSAP 3 wrap() / wrapYoyo() utilities</h2>
<div id="ball1" class="ball flair flair--2"></div>
<div id="ball2" class="ball flair flair--4"></div>

```

```
body{
  display:flex;
  align-items:stretch;
  justify-content:space-around;
  min-height:100vh;
  flex-direction: column;
}

.ball {
  width: 100px;
  height: 100px;
  will-change: transform;
}

h2 {
  margin: 20px;
  text-align: center
}
```

```
gsap.defaults({duration:20, ease:"none"});

var windowWrap = gsap.utils.wrap(0, window.innerWidth),
    windowYoyo = gsap.utils.wrapYoyo(0, window.innerWidth);

gsap.to("#ball1", {
  x: 10000,
  modifiers: {
    x: x => windowWrap(parseFloat(x)) + "px"
  }
});

gsap.to("#ball2", {
  x: 10000,
  modifiers: {
    x: x => windowYoyo(parseFloat(x)) + "px"
  }
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

### Carousel Wrap[​](#carousel-wrap "Direct link to Carousel Wrap")

Have you ever built a carousel and wrestled with making it loop seamlessly? Perhaps you duplicated each asset or wrote some code that moved each item back to the beginning when it reached the end. With ModifiersPlugin you can get a seamless repeating carousel with a single `.to()` with a `stagger`! The example below tweens each box to a relative `x` position of `"+=500"`. Click the "show overflow" button to see each box get reset to `x: 0` when it goes beyond 500.

#### loading...

  CodePen Embed - ModifiersPlugin: seamless loop  

```
<div class="nav">
<label><input type="checkbox" name="overflow" id="overflow" value="1" /> Show overflow</label>
</div>
<div class="wrapper">
  <div class="boxes">
    <div class="box">1</div>
    <div class="box">2</div>
    <div class="box">3</div>
    <div class="box">4</div>
    <div class="box">5</div>
    <div class="box">6</div>
    <div class="box">7</div>
    <div class="box">8</div>
    <div class="box">9</div>
    <div class="box">10</div>
</div>
</div>
```

```
body {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  flex-direction: column;
}

.wrapper {
  width: 450px;
  height: 50px;
  position: relative;
  background: #ccc;
  overflow: hidden;
}

.wrapper::after {
  width: 448px;
  height: 48px;
  content: "";
  position: absolute;
  border: solid 1px white;
}

.box {
  width: 50px;
  height: 50px;
  position: absolute;
  background: red;
  font-size: 25px;
  line-height: 50px;
  text-align: center;
  color: var(--color-just-black);
}

.boxes {
  position: relative;
  left: -50px;
}

.nav {
  position: relative;
  text-align: center;

  color: white;
  font-size: 20px;
  margin: 20px 0;
}
```

```
var colors = ["#0ae448","#ff8709", "#9d95ff", "#00bae2"];

//initially colorize each box and position in a row
gsap.set(".box", {
  backgroundColor: (i) => colors[i % colors.length],
  x: (i) => i * 50
});


gsap.to(".box", {
  duration: 5,
  ease: "none",
  x: "+=500", //move each box 500px to right
  modifiers: {
    x: gsap.utils.unitize(x => parseFloat(x) % 500) //force x value to be between 0 and 500 using modulus
  },
  repeat: -1
});


//toggle overflow
const overflow = document.querySelector("#overflow");
overflow.addEventListener("change", applyOverflow);

function applyOverflow() {
  if(overflow.checked) {
    gsap.set(".wrapper", {overflow: "visible"});
  } else {
    gsap.set(".wrapper", {overflow: "hidden"});
  }
}
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

### Advanced demos[​](#advanced-demos "Direct link to Advanced demos")

We've only scratched the surface of what ModifiersPlugin can do. Our moderator [Blake Bowen](https://gsap.com/community/profile/21420-osublake/) has been putting this plugin to the test and has an [impressive collection of demos](https://codepen.io/collection/AWxOyk/) that will surely inspire you.

### Caveats:[​](#caveats "Direct link to Caveats:")

*   To modify CSS transform's `scale`, use `scaleX` and `scaleY` (since it's a shortcut for those). And use `rotation`, not `rotationZ`.
    
*   RoundPropsPlugin and SnapPlugin tap into the same mechanism internally as ModifiersPlugin (to maximize efficiency, minimize memory, and keep kb down). Think of a `roundProps` tween as just a shortcut that creates a modifier that applies `Math.round()`, thus you cannot do _both_`roundProps` and a modifier on the same property. It's easy to get that functionality, though, by just doing `Math.round()` inside the modifier function.
    

## FAQs[​](#faqs "Direct link to FAQs")

#### How do I include this plugin in my project?

Simply load GSAP's core - ModifiersPlugin is included automatically!

#### Do I need to register ModifiersPlugin?

Nope. ModifiersPlugin and other core plugins are built into the core and don't have to be registered.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
