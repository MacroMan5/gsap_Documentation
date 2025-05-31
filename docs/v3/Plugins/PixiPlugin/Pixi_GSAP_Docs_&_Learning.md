# Pixi | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/PixiPlugin/](https://gsap.com/docs/v3/Plugins/PixiPlugin/)  
**Last Updated:** 2025-05-23T00:19:12.739Z  
**Extracted:** 2025-05-31 16:56:03

---

# Pixi | GSAP | Docs & Learning

Quick Start

#### CDN Link

```
gsap.registerPlugin(PixiPlugin) 
```

#### Minimal usage

```
 gsap.to(graphics, { duration: 2, pixi: { lineColor: "purple" } });
```

PixiPlugin makes it much easier to animate things in [PixiJS](https://www.pixijs.com/), a popular canvas library that's extremely performant. Without the plugin, it's a tad cumbersome with certain properties because they're tucked inside sub-objects in PixiJS's API, like `object.position.x`, `object.scale.y`, `object.skew.x`, etc. Plus PixiJS defines rotational values in radians instead of degrees which isn't as intuitive for most developers and designers. PixiPlugin saves you a bunch of headaches:

```
//old way (without plugin):gsap.to(pixiObject.scale, { x: 2, y: 1.5, duration: 1 });gsap.to(pixiObject.skew, { x: (30 * Math.PI) / 180, duration: 1 });gsap.to(pixiObject, { rotation: (60 * Math.PI) / 180, duration: 1 });//new way (with plugin):gsap.to(pixiObject, {  pixi: { scaleX: 2, scaleY: 1.5, skewX: 30, rotation: 60 },  duration: 1,});
```

Notice **rotational values are defined in degrees, not radians**. Yay!

Be sure to include the PixiPlugin correctly:

```
import * as PIXI from "pixi.js";import { gsap } from "gsap";import { PixiPlugin } from "gsap/PixiPlugin";// register the plugingsap.registerPlugin(PixiPlugin);// give the plugin a reference to the PIXI objectPixiPlugin.registerPIXI(PIXI);
```

## PixiJS examples[​](#pixijs-examples "Direct link to PixiJS examples")

There are a bunch of GSAP-based examples in the [PixiJS documentation here](https://pixijs.io/examples/#/gsap3-interaction/gsap3-basic.js)! It's a great place to start.

## Colors[​](#colors "Direct link to Colors")

PixiJS requires that you define color-related values in a format like `0xFF0000` but with PixiPlugin, you can define them the same way you would in CSS, like `"red"`, `"#F00"`, `"#FF0000"`, `"rgb(255,0,0)"`, `"hsl(0, 100%, 50%)"`, or `0xFF0000`. You can even do relative HSL values! `"hsl(+=180, +=0%, +=0%)"`.

```
//named colorsgsap.to(graphics, { duration: 2, pixi: { lineColor: "purple" } });//relative hsl() color that reduces brightness but leaves the hue and saturation the same:gsap.to(graphics, {  duration: 2,  pixi: { fillColor: "hsl(+=0, +=0%, -=30%)" },});
```

## ColorMatrixFilter[​](#colormatrixfilter "Direct link to ColorMatrixFilter")

Another big convenience is that PixiPlugin recognizes some special values like `saturation`, `brightness`, `contrast`, `hue`, and `colorize` (which all leverage a `ColorMatrixFilter` under the hood).

```
var image = new PIXI.Sprite.from(  "http://pixijs.github.io/examples/required/assets/panda.png");app.stage.addChild(image);var tl = gsap.timeline({ defaults: { duration: 2 } });//colorize fully red. Change colorAmount to 0.5 to make it only halfway colorized, for example:tl.to(image, { pixi: { colorize: "red", colorizeAmount: 1 } })  //change the hue 180 degrees (opposite)  .to(image, { pixi: { hue: 180 } })  //completely desaturate  .to(image, { pixi: { saturation: 0 } })  //blow out the brightness to double the normal amount  .to(image, { pixi: { brightness: 2 } })  //increase the contrast  .to(image, { pixi: { contrast: 1.5 } });
```

#### loading...

  CodePen Embed - PixiPlugin for GSAP v3  

```
<link href='//fonts.googleapis.com/css?family=Signika+Negative:300,400' rel='stylesheet' type='text/css'>

<div class="wrapper">
  
  <h2>PixiPlugin Filter Effects</h2>
  <div class="demo">
  <img src="https://assets.codepen.io/16327/car-dashboard-blur.jpg" width="300" height="300" cross-origin="anonymous">
  <canvas id="PixiApp" width="300" height="300"></canvas>
  </div>
  
  <pre class="code prettyprint lang-js">//sample code</pre>
  <div class="nav"></div>
  <form>
  <div>
    <input type="checkbox" id="combineCMF" name="combineCMF" value="false">
    <label for="combineCMF">combineCMF:true</label>
  </div>
    <p class="explanation">When combineCMF is set to true, the newly applied ColorMatrixFilter will preserve any previously-set "hue", "saturation", "brightness", "contrast", and "colorize" values. So if you desaturate the image and then increase brightness you will get a very bright grayscale image. However, if you desaturate the image and then click "colorize red" or "hue 180" you will not see any color change as the image will still have saturation of 0. combineCMF is false by default.</p>
</form>
  
  
</div>
```

```
/* Global styles come from external css https://codepen.io/GreenSock/pen/JGaKdQ*/
button {
  margin:0 6px 6px 0;
  padding: 9px 18px;
}
.explanation {
  font-weight: 300;
}



/*
 * Derived from einaros's Sons of Obsidian theme at
 * http://studiostyl.es/schemes/son-of-obsidian by
 * Alex Ford of CodeTunnel:
 * http://CodeTunnel.com/blog/post/71/google-code-prettify-obsidian-theme
 */

.str
{
    color: #EC7600;
}
.kwd
{
    color: #93C763;
}
.com
{
    color: #66747B;
}
.typ
{
    color: #678CB1;
}
.lit
{
    color: #FACD22;
}
.pun
{
    color: #F1F2F3;
}
.pln
{
    color: #9a8297;
}
.tag
{
    color: #8AC763;
}
.atn
{
    color: #E0E2E4;
}
.atv
{
    color: #EC7600;
}
.dec
{
    color: purple;
}
pre.prettyprint
{
    border: 0px solid #888;
}
ol.linenums
{
    margin-top: 0;
    margin-bottom: 0;
}
.prettyprint {
    background: #000;
}
li.L0, li.L1, li.L2, li.L3, li.L4, li.L5, li.L6, li.L7, li.L8, li.L9
{
    color: #555;
    list-style-type: decimal;
}
li.L1, li.L3, li.L5, li.L7, li.L9 {
    background: #111;
}
@media print
{
    .str
    {
        color: #060;
    }
    .kwd
    {
        color: #006;
        font-weight: bold;
    }
    .com
    {
        color: #600;
        font-style: italic;
    }
    .typ
    {
        color: #404;
        font-weight: bold;
    }
    .lit
    {
        color: #044;
    }
    .pun
    {
        color: #440;
    }
    .pln
    {
        color: #000;
    }
    .tag
    {
        color: #006;
        font-weight: bold;
    }
    .atn
    {
        color: #404;
    }
    .atv
    {
        color: #060;
    }
}

pre.prettyprint.code {
  padding:10px;
  margin-left:0px;
}

button:hover {
  background-color: #333;
  background-image: none;
}
```

```
var image, currentButton, 
    combineCMF = false;
var app = new PIXI.Application({
    width:300,
    height:300,
    backgroundColor: 0x000000, 
    autoResize: true, 
    view:document.getElementById("PixiApp")
});

function createEffect(name, code, onVars, offVars){
  var button = $("<button/>").text(name).appendTo(".nav"),
      style = button[0].style;
  button[0]._enabled = false;
  button.click(function() {
    var isEnabled = !this._enabled;
    if (!combineCMF || name === "reset") {
      $(".nav button").each(function() {
        this.style.removeProperty("background-image");
        this.style.removeProperty("background-color");
        this._enabled = false;
      });
    }
    currentButton = this;
    this._enabled = isEnabled;
    var vars = isEnabled ? onVars : offVars;
    vars.combineCMF = combineCMF;
    gsap.to(image, {duration:1, pixi:vars});
    if (isEnabled) {
      style.backgroundImage = "none";
      style.backgroundColor = "#4e9816";
      $(".code").text("gsap.to(image, {duration: 1, pixi:{" + code + ((combineCMF && name.indexOf("blur") === -1 && name !== "reset")  ? ", combineCMF:true" : "") + "}});").removeClass("prettyprinted");
    } else {
      gsap.set(this, {clearProps:"backgroundImage,backgroundColor"});
    }
    
    PR.prettyPrint(); 
  });
}

//toggle combineCMF
$('#combineCMF').click(function(){
  combineCMF = $(this).is(':checked');
  if (currentButton) {
    currentButton.click();
  }
});


image = PIXI.Sprite.from("https://assets.codepen.io/16327/car-dashboard-blur.jpg"); //previously used this, but ran into CORS issues: new PIXI.Sprite(resources.image.texture);
image.width = image.height = 300;
app.stage.addChild(image);
createEffect("colorize red", 'colorize:"red", colorizeAmount:1', {colorize:"red", colorizeAmount:1}, {colorize:"red", colorizeAmount:0});
createEffect("desaturate", "saturation:0", {saturation:0}, {saturation:1});
createEffect("hue 180", 'hue:180', {hue:180}, {hue:0});
createEffect("brightness", 'brightness:3', {brightness:3}, {brightness:1});
createEffect("contrast", 'contrast:3', {contrast:3}, {contrast:1});
createEffect("blur", 'blur:20', {blur:10}, {blur:0});
createEffect("reset", 'colorMatrixFilter:null, blur:0', {colorMatrixFilter:null, blur:0}, {colorMatrixFilter:null, blur:0});


```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

### External CSS

1.  [//codepen.io/GreenSock/pen/JGaKdQ.css](https://codepen.io/GreenSock/pen/JGaKdQ.css)

### External JavaScript

1.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.6.0/gsap.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.6.0/gsap.min.js)
2.  [//cdnjs.cloudflare.com/ajax/libs/jquery/3.1.1/jquery.min.js](https://cdnjs.cloudflare.com/ajax/libs/jquery/3.1.1/jquery.min.js)
3.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.6.0/TextPlugin.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.6.0/TextPlugin.min.js)
4.  [//cdnjs.cloudflare.com/ajax/libs/pixi.js/5.0.2/pixi.min.js](https://cdnjs.cloudflare.com/ajax/libs/pixi.js/5.0.2/pixi.min.js)
5.  [https://cdnjs.cloudflare.com/ajax/libs/gsap/3.6.0/PixiPlugin.min.js](https://cdnjs.cloudflare.com/ajax/libs/gsap/3.6.0/PixiPlugin.min.js)
6.  [//s3-us-west-2.amazonaws.com/s.cdpn.io/16327/prettyprint.js](https://s3-us-west-2.amazonaws.com/s.cdpn.io/16327/prettyprint.js)

Or if you have a custom `ColorMatrixFilter`, just pass that in as the `colorMatrixFilter` property and it'll handle animating between states:

```
var filter = new PIXI.filters.ColorMatrixFilter();filter.sepia();gsap.to(image, { pixi: { colorMatrixFilter: filter }, duration: 2 });
```

## BlurFilter[​](#blurfilter "Direct link to BlurFilter")

PixiPlugin recognizes `blur`, `blurX`, and `blurY` properties, so it's very simple to apply a blur without having to create a new `BlurFilter` instance, add it to the filters array, and animate its properties separately.

```
//blur on both the x and y axis to a blur amount of 15gsap.to(image, { pixi: { blurX: 15, blurY: 15 }, duration: 2 });
```

## Directional rotation[​](#directional-rotation "Direct link to Directional rotation")

You can control which direction a rotation tween goes by appending a suffix for **clockwise** (`"_cw"`), **counter-clockwise** (`"_ccw"`), or the **shortest direction** (`"_short"`). For example, if the element's rotation is currently 170 degrees and you want to tween it to -170 degrees, a normal rotation tween would travel a total of 340 degrees in the counter-clockwise direction, but `rotation: "-170_short"` suffix, it would travel 20 degrees in the clockwise direction instead! Example:

```
gsap.to(element, {  pixi: { rotation: "-170_short" },  duration: 2,});
```

Directional rotation capabilities were added in GSAP 3.2, so make sure you've got the latest update.

## Other properties[​](#other-properties "Direct link to Other properties")

PixiPlugin can handle almost any other property as well - there is no pre-determined list of "allowed" properties. PixiPlugin simply improves developer ergonomics for anyone animating in PixiJS. Less code, fewer headaches, and faster production. For a full listing of properties that the PixiPlugin helps with, see [the PixiPlugin Typescript declarations](https://github.com/greensock/GSAP/blob/master/types/pixi-plugin.d.ts).

## **Methods**[​](#methods "Direct link to methods")

|     |     |
| --- | --- |
| #### [PixiPlugin.registerPIXI](https://gsap.com/docs/v3/Plugins/PixiPlugin/static.registerPIXI\(\))( PIXI:Object ) ; | Registers the main PIXI library object with the PixiPlugin so that it can find the necessary classes/objects. You only need to register it once. |

---

*This documentation was extracted from the database for URLs containing 'gsap'*
