# static-convertToPath | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/MorphSVGPlugin/static.convertToPath](https://gsap.com/docs/v3/Plugins/MorphSVGPlugin/static.convertToPath)  
**Last Updated:** 2025-05-23T00:31:06.019Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-convertToPath | GSAP | Docs & Learning

## MorphSVGPlugin.convertToPath

### MorphSVGPlugin.convertToPath( shape:\[Element | String\], swap:Boolean ) : Array

Converts SVG shapes like `<circle>`, `<rect>`, `<ellipse>`, or `<line>` into `<path>`

#### Parameters

*   #### **shape**: \[Element | String\]
    
    An element or a selector string.
    
*   #### **swap**: Boolean
    
    By default, the resulting <path> will be swapped directly into the DOM in place of the provided shape element, but you can define `false` for `swap` to prevent that.
    

### Returns : Array[​](#returns--array "Direct link to Returns : Array")

Returns an Array of all `<path>` elements that were created.

### Details[​](#details "Direct link to Details")

Technically it's only feasible to morph `<path>` elements or `<polyline>`/`<polygon>` elements, but there are plenty of times you will want to morph a `<circle>`, `<rect>`, `<ellipse>`, or `<line>`. This method makes that possible by converting those basic shapes into `<path>` elements. It can be used like so:

```
MorphSVGPlugin.convertToPath("#elementID");
```

You can pass in an element or selector text, so you could also have it convert ALL of those elements with one line:

```
MorphSVGPlugin.convertToPath("circle, rect, ellipse, line, polygon, polyline");
```

This literally swaps in a `<path>` for each one directly in the DOM, and it should look absolutely identical. It'll keep the attributes like "id", etc. intact so that the conversion, you should be able to target the elements just as you would before.

```
//An svg <rect> Like this:<rect id="endShape" width="100" height="100" fill="red"/>//becomes<path id="endShape" fill="red" d="M100,0 v100 h-100 v-100 h100z"></path>
```

Why not automatically do the conversion? Because that's a bit too intrusive and could cause problems. For example, if you had event listeners applied to the original element(s) or references in your own code to those elements. We feel it's best to make sure the developer is aware of and specifically requests this conversion rather than doing it automatically.

#### loading...

  CodePen Embed - MorphSVG : convertToPath()  

```
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 760 400">
  <defs>
    <linearGradient id="grad-1" x1="200" y1="300" x2="255" y2="0" gradientUnits="userSpaceOnUse">
      <stop offset="0" stop-color="#f8dbb9"></stop>
      <stop offset="0.5" stop-color="#fb8305"></stop>
    </linearGradient>
    
    <linearGradient id="grad-2" x1="340" y1="42" x2="240" y2="125" gradientUnits="userSpaceOnUse">
      <stop offset="0.1" stop-color="#f8dbb9"></stop>
      <stop offset="0.5" stop-color="#fb8305"></stop>
    </linearGradient>
    
    <radialGradient id="grad-3" cx="460" cy="280" gradientUnits="userSpaceOnUse">
      <stop offset="0.1" stop-color="#f8dbb9"></stop>
      <stop offset="0.35" stop-color="#fb8305"></stop>
    </radialGradient>
    
    <g id="letters">
      <path id="a" d="M222.8 264.5c0-.7.2-1.6.6-2.8l48.4-134.1c.7-2.2 3.4-3.3 8.2-3.3h6c4.7 0 7.4 1.1 8 3.3l48.4 134.3c.5 1 .7 1.8.7 2.6 0 2.3-3 3.5-8.8 3.5h-1.7c-4.7 0-7.4-1-8.1-3.3l-12-33.4h-60l-11.7 33.4c-.7 2.2-3.4 3.3-8.2 3.3h-1c-5.8 0-8.8-1.2-8.8-3.5zm35.3-48.8H307L285.5 155l-2.7-11.8-3.2 11.8-21.5 60.8z"/>
      <path id="b" d="M364.6 262.9V132.3c0-4.1 2-6.2 6-6.2h36.6c14.9 0 26.2 3.3 34 9.8a32.5 32.5 0 0 1 11.7 26.4c0 6.8-2.2 13.2-6.7 19.4a29 29 0 0 1-15.7 11.6v.8a53.3 53.3 0 0 1 18.7 10.3c2.5 2.3 4.8 5.5 6.8 9.7s3 8.9 3 13.9c0 27.3-17.7 41-53.2 41h-35.1c-4 0-6.1-2-6.1-6.1zm18-75.1h23.6c8.2 0 15-2.3 20.2-7 5.3-4.6 8-10.5 8-17.6 0-7.2-2.3-12.5-7-16.1-4.6-3.6-12-5.4-22-5.4h-22.9v46zm0 65.7h29.7c9 0 16-2.3 20.8-7a25 25 0 0 0 7.4-19c0-7.8-2.7-13.8-8-18a38 38 0 0 0-23.6-6.2h-26.4v50.2z"/>
      <path id="c" d="M471.7 197.7c0-48.5 22-72.7 66.2-72.7a82 82 0 0 1 26.8 4.2c8.1 2.8 12.1 5.6 12.1 8.5 0 1.9-.8 4.3-2.5 7.3s-3.2 4.5-4.4 4.5c-.3 0-1.7-.8-4.4-2.3a59.3 59.3 0 0 0-27.2-6.7c-16.5 0-28.6 4.6-36.4 13.7-7.7 9.1-11.6 23.6-11.6 43.4s3.9 34.2 11.5 43.4c7.7 9.2 19.6 13.8 35.7 13.8a66.6 66.6 0 0 0 30-7.7 25 25 0 0 1 5-2.5c1.3 0 2.8 1.5 4.6 4.5 1.7 3 2.6 5.2 2.6 6.5 0 3.2-4.2 6.4-12.7 9.7-8.6 3.4-18.4 5-29.5 5-22.5 0-39-5.9-49.7-17.6-10.7-11.8-16-30.1-16-55z"/>
    </g>    
  </defs>
  
  <polygon id="triangle" fill="url(#grad-1)" points="241,242 283,157 326,242 "/>

  <rect id="square" fill="url(#grad-2)" x="363" y="157" width="85" height="85"/>
  
  <circle id="circle" fill="url(#grad-3)" cx="530" cy="200" r="42.5"/>

</svg>
```

```
body {
  width:100%;
  height:100vh;
  margin:0;
  padding:0;
  background:#0e100f;
  display:flex;
  align-items:center;
  justify-content:center;
}

svg {  
  max-width:1200px;
}
```

```
MorphSVGPlugin.convertToPath("circle, rect, polygon");

const tl = gsap
  .timeline({
    repeat: 20,
    repeatDelay: 0.5,
    delay: 0.5,
    yoyo: true,
    defaults: { ease: "power2.inOut" }
  })
  .to("#triangle", { morphSVG: "#a" })
  .to("#square", { morphSVG: "#b" })
  .to("#circle", { morphSVG: "#c" });
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

## Notes[​](#notes "Direct link to Notes")

*   If you define an `rx` or `ry` attribute on a `<rect>` element, make sure you define **both** (MorphSVGPlugin will default to a value of 0 whereas some browsers default to copying the one that was defined).

---

*This documentation was extracted from the database for URLs containing 'gsap'*
