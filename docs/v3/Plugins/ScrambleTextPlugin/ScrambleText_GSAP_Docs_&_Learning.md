# ScrambleText | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/ScrambleTextPlugin](https://gsap.com/docs/v3/Plugins/ScrambleTextPlugin)  
**Last Updated:** 2025-05-23T00:19:13.620Z  
**Extracted:** 2025-05-31 16:56:03

---

# ScrambleText | GSAP | Docs & Learning

Quick Start

#### CDN Link

```
gsap.registerPlugin(ScrambleTextPlugin) 
```

#### Minimal usage

```
gsap.to(element, {  duration: 1,   scrambleText: "THIS IS NEW TEXT"});
```

#### loading...

  CodePen Embed - Scramble Text  

```
<div class="text-scramble__content">
  <p id="scramble-text-original">Mix it up with ScrambleText. Animate using characters, numbers, UPPERCASE or lowercase.</p>

  <p class="text-scramble__text" aria-hidden="true">
    <span id="scramble-text-1"></span>
    <span id="scramble-text-2"></span>
    <span id="scramble-text-3"></span>
    <span id="scramble-text-4"></span>
    <span id="scramble-text-5"></span>

    <img id="scramble-cursor" src="https://assets.codepen.io/16327/scramble-cursor.png" alt="" />
  </p>
</div>
```

```
@font-face {
  font-display: block;
  font-family: Mori;
  font-style: normal;
  font-weight: 600;
  src: url(https://assets.codepen.io/16327/PPMori-Regular.woff) format("woff");
}

html,
body {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 100vh;
  overflow: hidden;
}

body {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-family: "Mori";
  background: #0e100f;
  text-align: center;
  color: #dfdcff;
  line-height: 1;
}

.text-scramble__content {
  font-size: max(2rem, min(5.69579vw + 0.665049rem, 3rem));
  font-weight: 600;
  letter-spacing: -0.01em;
  line-height: 1.1;
  margin-top: max(2rem, min(2.0712vw + 1.51456rem, 4rem));
  padding-bottom: 1.1em;
  position: relative;
}

.text-scramble__text {
  bottom: 0;
  left: 0;
  position: absolute;
  right: 0;
  top: 0;
}

.text-scramble__text span {
  word-break: break-word;
}

.text-scramble__text img {
  display: inline-block;
  height: 0.9em;
  width: auto;
}
```

```
const tl = gsap.timeline({
  id: "text-scramble",
  defaults: { ease: "none" }
});

const cursorTl = gsap.timeline({ repeat: -1 });

gsap.set("#scramble-text-original", {
  opacity: 0
});

cursorTl
  .to("#scramble-cursor", {
    opacity: 0,
    duration: 0.5,
    ease: "none",
    delay: 0.2
  })
  .to("#scramble-cursor", {
    opacity: 1,
    duration: 0.5,
    ease: "none",
    delay: 0.2
  });

tl.to("#scramble-text-1", {
  scrambleText: {
    text: "Mix it up with ScrambleText.",
    chars: "lowerCase"
  },
  duration: 2
})
  .to("#scramble-text-2", {
    scrambleText: {
      text: "Animate using characters",
      chars: "XO",
      speed: 0.4
    },
    duration: 2
  })
  .to("#scramble-text-3", {
    scrambleText: { text: " numbers,", chars: "0123456789" },
    duration: 2
  })
  .to("#scramble-text-4", {
    scrambleText: { text: "UPPERCASE", chars: "upperCase", speed: 0.3 },
    duration: 1
  })
  .to("#scramble-text-5", {
    scrambleText: {
      text: "or lowercase.",
      chars: "lowerCase",
      speed: 0.3
    },
    duration: 1.5
  })
  .add(cursorTl);

window.onclick = () => tl.play(0); // click to replay

```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

## Description[​](#description "Direct link to Description")

Scrambles the text in a DOM element with randomized characters (uppercase by default, but you can define lowercase or a set of custom characters), refreshing new randomized characters at regular intervals while gradually revealing your new text (or the original text) over the course of the tween (left to right by default). Visually it looks like a computer decoding a string of text. Great for rollovers.

## **Config Object**[​](#config-object "Direct link to config-object")

You can simply pass a string of text directly as the `scrambleText` and it'll use the defaults for revealing it, or you can customize the settings by using a generic object with any of the following properties:

*   #### text[](#text)
    
    String - The text that should replace the existing text in the DOM element. If omitted (or if `"{original}"`), the original text will be used.
    
*   #### chars[](#chars)
    
    String - The characters that should be randomly swapped in to the scrambled portion the text. You can use `"upperCase"`, `"lowerCase"`, `"upperAndLowerCase"`, or a custom string of characters, like `"XO"` or `"TMOWACB"`, or `"jompaWB!^"`, etc. Default: `"upperCase"`.
    
*   #### tweenLength[](#tweenLength)
    
    Boolean - If the length of the replacement text is different than the original text, the difference will be gradually tweened so that the length doesn’t suddenly jump. For example, if the original text is 50 characters and the replacement text is 100 characters, during the tween the number of characters would gradually move from 50 to 100 instead of jumping immediatley to 100. However, if you’d prefer to have it immediately jump, set `tweenLength` to `false`. Default: `true`.
    
*   #### revealDelay[](#revealDelay)
    
    Number - If you’d like the reveal (unscrambling) of the new text to be delayed for a certain portion of the tween so that the scrambled text is entirely visible for a while, use revealDelay to define the time you’d like to elapse before the reveal begins. For example, if the tween’s duration is 3 seconds but you’d like the scrambled text to remain entirely visible for first 1 second of the tween, you’d set `revealDelay` to `1`. Default: `0`.
    
*   #### newClass[](#newClass)
    
    String - If you’d like the new text to have a particular class applied (using a tag wrapped around it), use `newClass: "YOUR_CLASS_NAME"`. This makes it easy to create a distinct look for the new text. Default: `null`.
    
*   #### oldClass[](#oldClass)
    
    String - If you’d like the **old** (original) text to have a particular class applied (using a tag wrapped around it), use `oldClass: "YOUR_CLASS_NAME"`. This makes it easy to create a distinct look for the old text. Default: `null`.
    
*   #### speed[](#speed)
    
    Number - Controls how frequently the scrambled characters are refreshed. The default is `1` but you could slow things down by using `0.2` for example (or any number). Default: `1`.
    
*   #### delimiter[](#delimiter)
    
    String - By default, each character is replaced one-by-one, but if you’d prefer to have things revealed word-by-word, you could use a delimiter of `" "` (space). Default: `""`.
    
*   #### rightToLeft[](#rightToLeft)
    
    Boolean - If `true` the text will be revealed from right to left. Default: `false`.
    

## Usage[​](#usage "Direct link to Usage")

```
//use the defaultsgsap.to(element, {duration: 1, scrambleText: "THIS IS NEW TEXT"});//or customize things:gsap.to(element, {  duration: 1,   scrambleText: {    text: "THIS IS NEW TEXT",     chars: "XO",     revealDelay: 0.5,     speed: 0.3,     newClass: "myClass"  }});
```

## **Demos**[​](#demos "Direct link to demos")

Check out the full collection of [text animation demos](https://codepen.io/collection/ExBwoK) on CodePen.

*   [
    
    ### The Police
    
    ](https://codepen.io/petebarr/pen/ZEYXrBK)
*   [
    
    ### GSAP ScrambleText on :hover/:focus
    
    ](https://codepen.io/jh3y/pen/mdNKWRb)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
