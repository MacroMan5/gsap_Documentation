# SplitText | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/SplitText/](https://gsap.com/docs/v3/Plugins/SplitText/)  
**Last Updated:** 2025-05-23T00:30:49.239Z  
**Extracted:** 2025-05-31 16:56:03

---

# SplitText | GSAP | Docs & Learning

Quick Start

#### CDN Link

```
gsap.registerPlugin(SplitText) 
```

#### Minimal usage

```
// split elements with the class "split" into words and characterslet split = SplitText.create(".split", { type: "words, chars" });// now animate the characters in a staggered fashiongsap.from(split.chars, {  duration: 1,   y: 100,       // animate from 100px below  autoAlpha: 0, // fade in from opacity: 0 and visibility: hidden  stagger: 0.05 // 0.05 seconds between each});
```

Or use the new `onSplit()` syntax available in v3.13.0+ to do the exact same thing:

```
SplitText.create(".split", {  type: "words, chars",  onSplit(self) {    gsap.from(self.chars, {      duration: 1,       y: 100,       autoAlpha: 0,       stagger: 0.05    });  }});
```

SplitText is a small JavaScript library that splits an HTML element's text into individual characters, words, and/or lines (each in its own, newly-created element), allowing you to create gorgeous staggered animations. It's highly configurable and smarter than other text splitting tools thanks to features like automatic screen reader accessibility, masking for reveal effects, responsive re-splitting, and much more.

Detailed Walkthrough - Major rewrite in `v3.13.0` - half the size, 14 new features!

SplitText Walkthrough - YouTube

## Features[​](#features "Direct link to Features")

Feature Highlights

The new v3.13.0+ features are marked below with "\*"

*   **Screen reader Accessibility**\* - Adds `aria-label` to the split element(s) and `aria-hidden` to the freshly-created line/word/character elements.
*   **Responsive re-splitting**\* - Avoid funky line breaks when resizing or when fonts load with `autoSplit` and `onSplit()`. Offers automatic cleanup and resuming of animations too!
*   **Slice right through nested elements**\* - Elements like `<span>`, `<strong>`, and `<a>` that span multiple lines are handled effortlessly with `deepSlice` so they don't stretch lines vertically.
*   **Masking**\* - Wrap characters, words or lines with an extra clipping element for easy mask/reveal effects.
*   **Integrates seamlessly** with GSAP's [`context()`](https://gsap.com/docs/v3/GSAP/gsap.context\(\)/), [`matchMedia()`](https://gsap.com/docs/v3/GSAP/gsap.matchMedia\(\)) and [`useGSAP()`](https://gsap.com/resources/React)
*   **Flexible targeting** - Apply your own class names to characters, words, or lines. Append `"++"` to auto-increment them (e.g. `word1`, `word2`, etc.). Enable `propIndex`\* to apply CSS variables like `--word: 3`.
*   **Ignore certain elements**\* - Perhaps you'd like to leave `<sup>` elements unsplit, for example.
*   **Supports emojis & more** - SplitText does an excellent job with foreign characters too.
*   **Revert anytime** - Restore the element's original `innerHTML` anytime with `revert()`
*   **Handle complex edge cases** with custom `RegExp`\* or `prepareText()`\*

## Splitting[​](#splitting "Direct link to Splitting")

### Basic Usage[​](#basic-usage "Direct link to Basic Usage")

Feed `SplitText.create()` the element(s) you'd like to split and it'll return a SplitText instance with `chars`, `words`, and `lines` properties where you can access the resulting elements.

```
// the target can be selector text, an element, or an Array of elementslet split = SplitText.create(".headline");// Array of characterssplit.chars// Array of wordssplit.words// Array of linessplit.lines
```

### Configuration[​](#configuration "Direct link to Configuration")

By default, SplitText will split by `type: "lines, words, chars"` (meaning lines, words, **and** characters) but to maximize performance you should really only split what you need. Use the configuration object to control exactly which components are split apart, or to adjust accessibility settings, or apply your own classes or even apply masking effects.

```
let split = SplitText.create(".split", {  type: "words, lines", // only split into words and lines (not characters)  mask: "lines", // adds extra wrapper element around lines with overflow: clip (v3.13.0+)  linesClass: "line++", // adds "line" class to each line element, plus an incremented one too ("line1", "line2", "line3", etc.)  // there are many other options - see below for a complete list});
```

## **Config Object Settings**[​](#config-object-settings "Direct link to config-object-settings")

*   #### aria\*[](#aria*)
    
    "auto" | "hidden" | "none" - SplitText can automatically add `aria` attributes to the split element(s) as well as the line/word/character elements to improve accessibility. The options are:
    
    *   `"auto"` (the default) - adds an [aria label](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) to the split element(s), populated by its `textContent`, and also adds [aria hidden](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden) to the line/word/character elements inside the split. This ensures that the text is accessible to the majority of screen readers. **This approach will not honor the semantics or functionality of nested elements.** If you need to ensure that links inside your text content are visible to screen readers, we recommend enabling `aria: "hidden"` and creating a duplicate screen reader-only copy of your text.
    *   `"hidden"`: adds [aria hidden](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden) to the split element and all of the line/word/character elements inside the split.
    *   `"none"` - does not add any `aria` attributes to the split element or the line/word/character elements inside the split.
    
    Default: `"auto"`
    
*   #### autoSplit\*[](#autoSplit*)
    
    Boolean - Helps avoid odd line breaks due to text reflow after the fonts finish loading or if the element's width changes. If `true`, SplitText will revert and re-split whenever the fonts finish loading or when **both** of the following conditions apply:
    
    1.  The width of the split element(s) changes
    2.  `"lines"` are split.
    
    SplitText will even `console.warn()` you if you try splitting before the fonts finish loading and you didn't set `autoSplit: true`
    
    #### Caution
    
    When using `autoSplit: true`, make sure to create any animations in an `onSplit()` callback so that the freshly-split line/word/character elements are the ones being animated. If you `return` the animation in the `onSplit()`, SplitText will automatically clean up and synchronize the animation on each re-split.
    
    ```
    SplitText.create(".split", {  type: "lines",  autoSplit: true,  onSplit: (self) => {    return gsap.from(self.lines, {      y: 100,      opacity: 0,      stagger: 0.05    });  }});
    ```
    
    Default: `false`
    
*   #### charsClass[](#charsClass)
    
    String - A CSS class applied to each character's `<div>`, making it easy to select. If you add `"++"` to the end of the class name, SplitText will also add a second class of that name but with an incremented number appended, starting at 1. For example, if `charsClass` is `"char++"`, the the first character would have `class="char char1"`, the next would have `class="char char2"`, then `class="char char3"`, etc. Default: `undefined`.
    
*   #### deepSlice\*[](#deepSlice*)
    
    Boolean - If a nested element like `<strong>` wraps onto multiple lines, SplitText subdivides it accordingly so that it doesn't expand the line vertically. So technically one nested element could be split up into multiple elements. This is only effective for splitting `lines`. Default: `true`.
    
*   #### ignore\*[](#ignore*)
    
    String | Element - Descendant elements to ignore when splitting (you may use selector text like `".split"` or an Array of elements). They will still exist - they simply won't be split [Demo here](https://codepen.io/GreenSock/pen/JojaebV) Default: `undefined`
    
*   #### linesClass[](#linesClass)
    
    String - A CSS class applied to each line's `<div>`, making it easy to select. If you add `"++"` to the end of the class name, SplitText will also add a second class of that name but with an incremented number appended, starting at 1. For example, if `linesClass` is `"line++"`, the the first line would have `class="line line1"`, the next would have `class="line line2"`, then `class="line line3"`, etc. Default: `undefined`.
    
*   #### mask\*[](#mask*)
    
    "lines" | "words" | "chars" - wraps every line or word or character in an _extra_ element with `visibility: clip` for much simpler reveal effects. Access them in a "masks" Array on the SplitText instance. If you set a class name for the lines/words/chars, it'll append `"-mask"` for easy selecting. You cannot mask multiple types, so this value should be either "lines" or "words" or "chars" but not a combination. Default: `undefined`
    
*   #### onRevert\*[](#onRevert*)
    
    Function - A function that gets called whenever the SplitText instance reverts
    
*   #### onSplit\*[](#onSplit*)
    
    Function - A function that gets called whenever the SplitText instance finishes splitting, including when `autoSplit: true` causes it to re-split, like when the fonts finish loading or when the width of the split element(s) changes (which often makes lines reflow). If you return a GSAP animation (tween or timeline), it will automatically save its `totalTime()` and `revert()` it when the SplitText reverts, and set the new animation's `totalTime()` that's returned in the `onSplit`, making it appear relatively seamless!
    
*   #### prepareText\*[](#prepareText*)
    
    Function - A function that gets called for each block of text as the split occurs, allowing you to modify each chunk of text right before SplitText runs its splitting logic. For example, you might want to insert some special characters marking where word breaks should occur. The `prepareText()` function receives the raw text as the first argument, and the parent element as the second argument. You should **return** the modified text. This can be useful for non-Latin languages like Chinese, where there are no spaces between words. [Demo here](https://codepen.io/GreenSock/pen/VYYvwoq/f30d0213097fe1c8c5a0a09215a5568f)
    
*   #### propIndex\*[](#propIndex*)
    
    Boolean - adds a CSS variable to each split element with its index, like `--word: 1`, `--word: 2`, etc. It works for all types (line, word, and char). Default: `false`
    
*   #### reduceWhiteSpace[](#reduceWhiteSpace)
    
    Boolean - Collapses consecutivewhite space characters into one, as most browsers typically do. Set to `false` if you prefer to maintain multiple consecutive white space characters. Since **v3.13.0** reduceWhiteSpace will honor extra spaces and automatically insert `<br>` tags for line breaks which is useful for `<pre>` content. Default: `true`
    
*   #### smartWrap\*[](#smartWrap*)
    
    Boolean - If you split by `"chars"` only, you can end up with odd breaks at the very end of lines when characters in the middle of a word flow onto the next line, untethered by natural word-grouping. `smartWrap: true` will wrap words in a `<span>` that has `white-space: nowrap` to keep them grouped (only when you're not splitting by words or lines). This will be ignored if you're splitting by `"words"` or `"lines"`, as it's unnecessary. Default: `false`
    
*   #### tag[](#tag)
    
    String - By default, SplitText wraps things in `<div>` elements, but you can define any tag like `tag: "span"`. Note that browsers won't render transforms like rotation, scale, skew, etc. on inline elements.
    
*   #### type[](#type)
    
    String - A comma-delimited list of the split type(s) which can be any combination of the following: `chars`, `words`, or `lines`. This indicates the type of components you’d like split apart into distinct elements. For example, to split apart the characters and words (not lines), you’d use `type: "chars,words"` or to only split apart lines, you’d do `type: "lines"`. In order to avoid odd line breaks, it is best to not split by chars alone (always include words or lines too if you're splitting by characters) or just set `smartWrap: true`. Note: spaces are not considered characters. Default: `"chars,words,lines"`.
    
*   #### wordDelimiter[](#wordDelimiter)
    
    RegExp | "string" | Object - Normally, words are split at every space character. The `wordDelimiter` property allows you to specify your own custom delimiter for words. For example, if you want to split a hashtag like **#IReallyLoveGSAP** into words, you could insert a zero-width word joiner character (`&#8205;`) between each word like: `#&#8205;I&#8205;Really&#8205;Love&#8205;GSAP` and then set `wordDelimiter: String.fromCharCode(8205)` in the SplitText config object. Since **v3.13.0**, you can specify where to split using a RegExp and also what text to swap in at those spots for ultimate flexibility like
    
    ```
    wordDelimiter: {delimiter: yourRegExp, replaceWith: "yourReplacement"}
    ```
    
    Default: `" "` (space)
    
*   #### wordsClass[](#wordsClass)
    
    String - A CSS class applied to each word's `<div>`, making it easy to select. If you add `"++"` to the end of the class name, SplitText will also add a second class of that name but with an incremented number appended, starting at 1. For example, if `wordsClass` is `"word++"`, the the first word would have `class="word word1"`, the next would have `class="word word2"`, then `class="word word3"`, etc. Default: `undefined`.
    

## Animating[​](#animating "Direct link to Animating")

#### loading...

  CodePen Embed - SplitText Demo  

```
<div class="container">
  <div class="button-wrapper">
    <button id="chars" class="button">Characters</button>
    <button id="words" class="button">Words</button>
    <button id="lines" class="button">Lines</button>
  </div>
  <div class="text">
    Break apart HTML text into characters, words, and/or lines for easy animation.
  </div>

</div>
```

```
html,
body {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  overflow: hidden;
}

.container {
  position: relative;
  width: 90vw;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  border-radius: 9px;
}

.text {
  color: #dfdcff;
  font-size: clamp(2rem, 12rem, 5vw);
  line-height: 1.2;
  box-sizing: border-box;
  padding: 5%;
  width: 100%;
  text-align: center;
  perspective: 500px;
}

.button-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  flex-wrap: wrap;
}
```

```
gsap.registerPlugin(SplitText);

let split, animation;
document.querySelector("#chars").addEventListener("click", () => {
  animation && animation.revert();
  animation = gsap.from(split.chars, {
    x: 150,
    opacity: 0,
    duration: 0.7, 
    ease: "power4",
    stagger: 0.04
  })
});

document.querySelector("#words").addEventListener("click", () => {
  animation && animation.revert();
  animation = gsap.from(split.words, {
    y: -100,
    opacity: 0,
    rotation: "random(-80, 80)",
    duration: 0.7, 
    ease: "back",
    stagger: 0.15
  })
});

document.querySelector("#lines").addEventListener("click", () => {
  animation && animation.revert();
  animation = gsap.from(split.lines, {
    rotationX: -100,
    transformOrigin: "50% 50% -160px",
    opacity: 0,
    duration: 0.8, 
    ease: "power3",
    stagger: 0.25
  })
});

function setup() {
  split && split.revert();
  animation && animation.revert();
  split = SplitText.create(".text", {type:"chars,words,lines"});
}
setup();
window.addEventListener("resize", setup);
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

Once your text is split, you can animate each line, word, or character using GSAP:

```
// split all elements with the class "split" into words and characterslet split = SplitText.create(".split", { type: "words, chars" });// now animate the characters in a staggered fashiongsap.from(split.chars, {  duration: 1,   y: 100,         // animate from 100px below  autoAlpha: 0,   // fade in from opacity: 0 and visibility: hidden  stagger: 0.05,  // 0.05 seconds between each});
```

Or use the new `onSplit()` syntax available in v3.13.0+ to do the exact same thing - the main benefit is that the code inside `onSplit()` will execute anytime the SplitText instance **re-splits** in the future (like if you set `autoSplit: true` or if you manually call `split()`):

```
SplitText.create(".split", {  type: "words, chars",  onSplit(self) { // runs every time it splits    gsap.from(self.chars, {      duration: 1,       y: 100,       autoAlpha: 0,       stagger: 0.05    });  }});
```

### Responsive Line Splitting\*[​](#responsive-line-splitting "Direct link to responsive-line-splitting")

If _only_ words and/or characters are split, they reflow naturally when the container resizes but if you split by **lines**, each line element encloses around a specific set of words/characters. If the container then resizes narrower _or_ if the font loads after the split, for example, the text may reflow causing some of the words to belong in _different_ lines (the last word in a line may shift down to the next). The only way to avoid strange line breaks is to re-split (restore the original `innerHTML` and have SplitText run its splitting logic again) so that the line elements enclose the proper words.

Don't worry! SplitText's `autoSplit` saves the day! 🥳 When enabled, it will revert and re-split when fonts finish loading or when **both** of the following conditions apply:

*   The width of the split element(s) changes
*   "lines" are split.

With `autoSplit` enabled, you should **always** create your animations in the `onSplit()` callback so that if it re-splits later, the resulting animations affect the freshly-created line/word/character elements instead of the ones from the previous split. If you **return** your [`tween`](https://gsap.com/docs/v3/Plugins/SplitText/docs/v3/GSAP/Tween/) or [`timeline`](https://gsap.com/docs/v3/Plugins/SplitText/docs/v3/GSAP/Timeline/) inside the `onSplit()` callback, your old animation will be safely `reverted()` before the new one is created and SplitText will automatically save the previous animation's `totalTime()` before reverting it, and apply it to the new one so that everything appears relatively seamless! The SplitText instance is passed to the `onSplit()` (below, we call it `self`) so you can access its properties:

```
// whenever you use autoSplit: true, ALWAYS create your animations in the onSplit()SplitText.create(".split", {    type: "words,lines",    autoSplit: true,    onSplit(self) {      return gsap.from(self.lines, { // a returned animation gets cleaned up and time-synced on each onSplit() call        yPercent: 20,        opacity: 0,        stagger: 1,        duration: 3,        onComplete: () => self.revert() // revert the element to its original (unsplit) state      });    }  });
```

#### loading...

  CodePen Embed - SplitText Demo from Youtube Video - responsive line splitting  

```
<nav>
  <button class="charButton">Toggle Character Borders</button><button class="wordButton">Toggle Word Borders</button><button class="lineButton">Toggle Line Borders</button>
</nav>

<div class="container">
  <h2 class="split">The text in this paragraph is split by words and lines. Lines can be tricky to manage responsively. In this demo we are solving this with autoSplit:true and onSplit. autoSplit is used to Split the text automatically when the text element resizes. We are then using the onSplit callback to revert the old animation, then on the new Split, creating a new animation with the progress preserved.
    So this is all you need to have a responsive line animation that resplits on resize.</h2>
</div>
```

```
@font-face {
  font-display: block;
  font-family: Mori;
  font-style: normal;
  font-weight: 900;
  src: url(https://assets.codepen.io/16327/PPMori-SemiBold.woff) format("woff");
}

:root {
  --color-shockingly-green: #0ae448;
  --color-just-black: #0e100f;
  --color-surface-white: #fffce1;
  --color-pink: #fec5fb;
  --color-shockingly-pink: #f100cb;
  --color-orangey: #ff8709;
  --color-lilac: #9d95ff;
  --color-lt-green: #abff84;
  --color-blue: #00bae2;
  --color-grey: gray;
  --color-surface75: #bbbaa6;
  --color-surface50: #7c7c6f;
  --color-surface25: #42433d;
  --gradient-macha: linear-gradient(
    114.41deg,
    var(--color-shockingly-green) 20.74%,
    var(--color-lt-green) 65.5%
  );
  --gradient-orange-crush: linear-gradient(
    111.45deg,
    var(--color-orangey) 19.42%,
    #f7bdf8 73.08%
  );
  --gradient-lipstick: linear-gradient(
    165.72deg,
    #f7bdf8 21.15%,
    #cd237f 81.93%
  );
  --gradient-purple-haze: linear-gradient(
    153.58deg,
    #f7bdf8 32.25%,
    #2f3cc0 92.68%
  );
  --gradient-skyfall: linear-gradient(
    131.77deg,
    #0a157a 30.82%,
    #15bfe4 81.82%
  );
  --gradient-emerald-city: linear-gradient(
    166.9deg,
    var(--color-shockingly-green) 53.19%,
    #0085d0 107.69%
  );
  --gradient-summer-fair: linear-gradient(
    144.02deg,
    var(--color-blue) 4.56%,
    var(--color-pink) 72.98%
  );
  --color-core-green: #dfffd1;
  --color-core-green-lt: #f3ffee;
  --color-core-gradient: radial-gradient(
    89.08% 84.62% at 16.54% 78.46%,
    #fbfefa 0%,
    #c9f6b4 39.58%,
    #abff84 77.6%,
    #2fee65 100%
  );
  --color-core-button-gradient: linear-gradient(
    114.41deg,
    #0ae448 20.74%,
    #abff84 65.5%
  );
  --color-core-heading-gradient: linear-gradient(
      180deg,
      #d6ffc3 0%,
      rgba(214, 255, 195, 0) 100%
    ),
    #f3ffee;
  --color-core-intro-gradient: linear-gradient(
      144.5deg,
      #e8ffdd 65.09%,
      #7dea7b 122.73%
    ),
    linear-gradient(311.31deg, #7ef89e 36.08%, #e5ffd9 106.98%);
  --color-text-purple: #d2ceff;
  --color-text-purple-lt: #dfdcff;
  --color-text-gradient: radial-gradient(
    129.03% 100% at 120.97% 81.45%,
    #dfdcff 27.08%,
    #a69eff 100%
  );
  --color-svg-tangerine: #ffe3c7;
  --color-svg-tangerine-lt: #fff0e0;
  --color-svg-gradient: radial-gradient(
    70.77% 70.77% at 0% 70.77%,
    #ffd9b0 0%,
    #fd9f3b 80.73%,
    #ff8709 100%
  );
  --color-svg-heading-gradient: linear-gradient(
      180deg,
      #ffbd77 0%,
      rgba(254, 197, 251, 0) 100%
    ),
    #ffe4c7;
  --color-ui-blue: #bef3fe;
  --color-ui-blue-lt: #e1faff;
  --color-ui-blue-codeblk: #f6feff;
  --color-ui-text-gradient: linear-gradient(
    168.89deg,
    #fec5fb -21.3%,
    #00bae2 89.88%
  );
  --color-ui-code-blocktext-gradient: linear-gradient(
    142.91deg,
    #cef6ff 18.75%,
    #a6efff 54.93%
  );
  --color-ui-gradient: radial-gradient(
    78.77% 78.77% at 71.71% 30.77%,
    #f0fcff 0%,
    #9bedff 67.21%,
    #98ecff 76.04%,
    #5be1ff 84.9%,
    #00bae2 94.79%
  );
  --color-ui-gradient-background: linear-gradient(
    137.1deg,
    #ecfcff 27.5%,
    #a6efff 94.09%
  );
  --color-ui-gradient-flip-background: radial-gradient(
    140% 190% at 117.54% 131.12%,
    #f0fcff 0%,
    #9bedff 25.52%,
    #98ecff 42.71%,
    #5be1ff 60.94%,
    #00bae2 94.79%
  );
  --color-scroll-pink: #ffd7fd;
  --color-scroll-pink-lt: #ffe9fe;
  --color-scroll-gradient: linear-gradient(
    317.42deg,
    #ffe9fe 10.4%,
    #ff96f9 83.03%
  );
  --ease-in: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-out: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-in-out: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-out-quart: cubic-bezier(0.175, 0.79, 0.38, 0.905);
  --ease-in-out-quart: cubic-bezier(0.645, 0.045, 0.355, 1);
}

:root {
  --dark: var(--color-just-black);
  --grey-dark: #42433d;
  --light: var(--color-surface-white);
  --mid: #7c7c6f;
  --grey: #gray;
  --gray: #gray;
  --green: var(--color-shockingly-green);
  --green-dark: #0ae448;
  --green-light: var(--color-lt-green);
  --blue: var(--color-blue);
  --purple: var(--color-lilac);
  --red: #cd237f;
  --orange: var(--color-orangey);
  accent-color: var(--color-shockingly-green);
}

html {
  background: radial-gradient(
      129% 99% at 112% 85%,
      rgb(223, 220, 255) 20%,
      rgb(166, 158, 255) 90%
    ),
    url("https://assets.codepen.io/16327/noise-e82662fe.png");
  background-blend-mode: color-dodge;
}

html,
body {
  margin: 0;
  padding: 0;
  width: 100%;
  min-height: 100vh;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  font-family: "Mori";
}

.container {
  width: 90vw;
}

.split {
  opacity: 0;
  text-align: center;
  color: rgb(14, 16, 15);
  font-size: 1.5rem;
  will-change: transform;
  color: #0e100f;
}

.split * {
  will-change: transform;
}

button {
  display: inline-block;
  outline: none;
  padding: 8px 14px;
  background: transparent;
  border: solid 2px var(--dark);
  color: var(--dark);
  text-decoration: none;
  border-radius: 99px;
  padding: 6px 12px;
  font-size: 0.6rem;
  text-transform: uppercase;
  font-weight: 600;
  cursor: pointer;
  line-height: 18px;
  margin: 0.25rem;
}
button.active {
  background: var(--dark);
  color: var(--light);
}



nav {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  padding: 1rem;
}


.chars .char {
  outline: 1px solid var(--dark);
}

.words .word {
  outline: 1px dashed var(--dark);
}

.lines .line {
  outline: 1px dashed var(--dark);
}
```

```
gsap.registerPlugin(SplitText);

console.clear();

document.fonts.ready.then(() => {
  gsap.set(".split", { opacity: 1 });

  let split = SplitText.create(".split", {
    type: "words, lines",
    linesClass: "line",
    wordsClass: "word",
    charsClass: "char",
    autoSplit: true,
    onSplit: (self) => {
      console.log("splitting");

      return gsap.from(self.lines, {
        yPercent: 20,
        opacity: 0,
        stagger: 0.05,
        duration: 3,
        repeat: -1
      });
    }
  });

  document.body.classList.add("lines");
});

document.querySelector(".charButton").addEventListener("click", () => {
  document.body.classList.toggle("chars");
});

document.querySelector(".wordButton").addEventListener("click", () => {
  document.body.classList.toggle("words");
});

document.querySelector(".lineButton").addEventListener("click", () => {
  document.body.classList.toggle("lines");
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

### Masking\*[​](#masking "Direct link to masking")

Masking wraps each line, word or character in an _extra_ element with `visibility: clip` for fun reveal effects.

```
SplitText.create(".split", {    type: "words,lines",    mask: "words", // <-- this can be "lines" or "words" or "chars"});
```

#### loading...

  CodePen Embed - Masked Lines with SplitText  

```
<div class="container">
  <h1 class="split">The text in this paragraph is split by words and lines. We have enabled masking on the lines so that we can animate the lines to create a fun 'reveal' animation. Nice and easy!</h1>
</div>

<button>Replay Slowly</button>
```

```
@font-face {
  font-display: block;
  font-family: Mori;
  font-style: normal;
  font-weight: 900;
  src: url(https://assets.codepen.io/16327/PPMori-SemiBold.woff) format("woff");
}

html, body {
  margin:0;
  padding:0;
  width:100%;
  height:100vh;
}
  
body {
  display:flex;
  align-items:center;
  justify-content:center;
  flex-direction: column;
  font-family: "Mori";
/*   background: #0e100f; */
  background: radial-gradient(129% 99% at 112% 85%, rgb(223, 220, 255) 20%, rgb(166, 158, 255) 90%),    
    url('https://assets.codepen.io/16327/noise-e82662fe.png');  
  background-blend-mode: color-dodge;
}

.container {
  max-width: 80vw;
}

.split {
  opacity: 0;
  text-align:center;
  color: rgb(14, 16, 15);
  font-size: clamp(2rem, 5rem, 3vw);
  letter-spacing: 0.05rem;
  will-change: transform;
  color: #0e100f;
}

.split * {
  will-change: transform;
}

button {
  display: inline-block;
  outline: none;
  padding: 8px 14px;
  background: transparent;
  border: solid 4px #0e100f;
  color: #0e100f;
  text-decoration: none;
  border-radius: 99px;
  padding: 12px 25px;
  text-transform: uppercase;
  font-weight: 600;
  cursor: pointer;
  line-height: 18px;
}
```

```
gsap.registerPlugin(SplitText);

console.clear();

document.fonts.ready.then(() => {
  gsap.set(".split", { opacity: 1 });

  let split;
  SplitText.create(".split", {
    type: "words,lines",
    linesClass: "line",
    autoSplit: true,
    mask: "lines",
    onSplit: (self) => {
      split = gsap.from(self.lines, {
        duration: 0.6,
        yPercent: 100,
        opacity: 0,
        stagger: 0.1,
        ease: "expo.out",
      });
      return split;
    }
  });

  document.querySelector("button").addEventListener("click", (e) => {
    split.timeScale(0.2).play(0);
  });
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

## Screen Reader Accessibility[​](#screen-reader-accessibility "Direct link to Screen Reader Accessibility")

People who are blind or partially-sighted might use a screen reader which analyzes the content of a site and converts it into speech to help them navigate a website. A screen reader would see the following heading tag and read it out loud.

Most text splitting libraries simply divide the text into divs which screen readers verbalize **painfully** slowly, letter by letter...

```
<h1>  <div>H</div>  <div>e</div>  <div>a</div>  <div>d</div>  <div>i</div>  <div>n</div>  <div>g</div></h1>
```

### Built-in Aria\*[​](#built-in-aria "Direct link to built-in-aria")

To get around this issue, SplitText adds an [`aria-label`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-label) to the parent element and then hides the child elements with [`aria-hidden`](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/Reference/Attributes/aria-hidden). This ensures that when visually impaired people navigate your site, screen readers will read the `aria-label` instead of the contents of the split elements. 🥳 This approach works for the majority of use-cases and is enabled by default.

```
<h2 aria-label="My Accessible Heading">  <div aria-hidden="true">My</div>  <div aria-hidden="true">Accessible</div>  <div aria-hidden="true">Heading</div></h2>
```

### Alternate Strategy for Maximizing Nested Element Accessibility[​](#alternate-strategy-for-maximizing-nested-element-accessibility "Direct link to Alternate Strategy for Maximizing Nested Element Accessibility")

SplitText's built in `aria: "auto"` solution is ideal for most common scenarios, but it won't surface the functionality and meaning of nested elements (like links) to screen readers. If you have complex nested text, you can use the duplication approach described below. Exercise restraint here as duplicating lots of DOM elements can lead to performance lags.

Treat text splitting with care and ensure you test thoroughly!

In the example below, the link may not be recognized as such by some screen readers:

```
<h2 aria-label="This link isn't accessible">  <div aria-hidden="true">This</div>  <div aria-hidden="true"><a href="#">link</a></div>  <div aria-hidden="true">isn't</div>  <div aria-hidden="true">accessible</div></h2>
```

If you need to preserve the semantics and functionality of nested elements - like links, `<strong>` tags or `<em>` tags - we recommend disabling the default aria settings for the SplitText with `aria: "none"`\*, and creating a [screen reader-only](https://css-tricks.com/inclusively-hidden/) duplicate of your element instead. This way, sighted users will see the animated text, while visually impaired people will get the screenreader-only content announced to them.

#### loading...

  CodePen Embed - Accessible text by duplication  

```
<div class="container">
  <div class="animate-me" aria-hidden="true">
    This text has a <a href="https://testlink.com">nested link</a> so we have created a duplicate "screenreader-only" element to preserve the semantics of child elements for screenreaders.
  </div>
  <p class="sr-only">
    This text has a <a href="https://testlink.com">nested link</a> so we have created a duplicate "screenreader-only" element to preserve the semantics of child elements for screenreaders.
  </p>
</div>
```

```
/* Hiding class, making content visible only to screen readers but not visually */
/* "sr" meaning "screen-reader" */
/* https://css-tricks.com/inclusively-hidden/ */
.sr-only:not(:focus):not(:active) {
  clip: rect(0 0 0 0); 
  clip-path: inset(50%);
  height: 1px;
  overflow: hidden;
  position: absolute;
  white-space: nowrap; 
  width: 1px;
}

html, body {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}

.container {
  position: relative;
  width: 90vw;
  height: 90vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-evenly;
  border-radius: 9px;
  opacity: 0;
}

.animate-me {
  color: #dfdcff;
  font-size: 25px;
  box-sizing: border-box;
  padding: 5%;
  width: 100%;
  text-align: left;
  perspective: 500px;
}

a {
  color: var(--color-orangey)
}
```

```
gsap.registerPlugin(SplitText);

document.fonts.ready.then(() => {
  gsap.set(".container", { opacity: 1 });
  let split = SplitText.create(".animate-me", { type: "words", aria: "hidden" });

  gsap.from(split.words, {
    opacity: 0,
    duration: 2,
    ease: "sine.out",
    stagger: 0.1,
  });
});
```

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

## Reverting[​](#reverting "Direct link to Reverting")

Performance-wise, it can be expensive for browsers to render a lot of nodes/elements, so it's often a good idea to `revert()` your split elements to their original state when you're done animating them. Simply call `revert()` on the SplitText instance to restore the original `innerHTML`:

```
let split = SplitText.create(".split", {type: "words"});gsap.from(split.words, {  x: "random(-100, 100)",  y: "random(-100, 100)",  stagger: 0.1,  onComplete: () => split.revert() // <-- restores original innerHTML})
```

## Tips & Limitations[​](#tips--limitations "Direct link to Tips & Limitations")

Tips & Limitations

*   **Characters shift slightly when splitting?** - Some browsers apply kerning between certain characters which is lost when each character is put into its own element, thus the spacing shifts slightly. You can typically eliminate that shift by disabling the kerning with this CSS:
    
    ```
    font-kerning: none; text-rendering: optimizeSpeed;
    ```
    
*   **Custom Fonts** - If you split before your web fonts are ready, the layout may shift or misalign. To avoid this, either:
    
    *   Wait for the fonts to load before splitting by placing your code inside `document.fonts.ready.then(() => {...your code here...})`, or
    *   Set `autoSplit: true` to have SplitText re-split once fonts finish loading. Don't forget to put your animation code inside the `onSplit()` callback!
*   **Only split what you need** - Splitting thousands of elements can be expensive. If you’re only animating words or lines, skip splitting characters for better performance.
    
*   **SEO** - If you split your main `<h1/>` element, ensure that your page has the appropriate title and description meta tags and your SplitText has `aria: "auto"` (default) enabled. Without these your split heading may appear in google search results in it's composite parts.
    
*   **Avoid text-wrap: balance** - it interferes with clean text splitting.
    
*   **SVG** - SplitText is not designed to work with SVG `<text>` nodes.
    
*   **Standalone plugin** - SplitText is one of the only GSAP plugins that _can_ be used **without** loading GSAP's core.
    

## **Demos**[​](#demos "Direct link to demos")

Check out the full collection of [text animation demos](https://codepen.io/collection/ExBwoK) on CodePen.

*   [
    
    ### scramble cursor effect
    
    ](https://codepen.io/creativeocean/pen/NPWLwJM)
*   [
    
    ### Secret scramble reveal
    
    ](https://codepen.io/ZachSaucier/pen/QwWVaMo)
*   [
    
    ### AutoSplit
    
    ](https://codepen.io/GreenSock/pen/azzvbYL/2f1edfd9d9462aa26150669eb528fb5f)
*   [
    
    ### Devengari - smart splitting
    
    ](https://codepen.io/GreenSock/pen/KoJOJb?editors=0010)
*   [
    
    ### Revert onComplete
    
    ](https://codepen.io/GreenSock/pen/poZaJQa)
*   [
    
    ### Masked Lines
    
    ](https://codepen.io/GreenSock/pen/LEYqezo/a28f78aa1b47e6fa3ad56684564fdf81)
*   [
    
    ### Responsive line splits on scroll
    
    ](https://codepen.io/GreenSock/pen/GggpRoB/4102c8975752c2f62811e8beaa4a5948)
*   [
    
    ### PrepareText - chinese
    
    ](https://codepen.io/GreenSock/pen/VYYvwoq/f30d0213097fe1c8c5a0a09215a5568f?editors=1010)
*   [
    
    ### Ignored Elements
    
    ](https://codepen.io/GreenSock/pen/JojaebV)
*   [
    
    ### Simple wordDelimiter
    
    ](https://codepen.io/GreenSock/pen/jEEbzJb/05ee2e789dac10d9c7e7864c1d776802)
*   [
    
    ### Word Delimiter with RegExp
    
    ](https://codepen.io/GreenSock/pen/LEEpdKr/1e99e544497401e5ae18d8a5770f1963)
*   [
    
    ### Masked Letters
    
    ](https://codepen.io/GreenSock/pen/JooXdwP/0426766204071a076b91ec83bf7fe52f)
*   [
    
    ### Screenreader only duplicate text
    
    ](https://codepen.io/GreenSock/pen/RNNabZr/12697152a77fa81cefd0e6bb3d87c2da)
*   [
    
    ### SciFi Stuff
    
    ](https://codepen.io/marioluevanos/pen/XKqNZB)
*   [
    
    ### modulofont
    
    ](https://codepen.io/benoitwimart/pen/NWxWYYN?editors=0010)
*   [
    
    ### Dance With Me
    
    ](https://codepen.io/elegantseagulls/pen/wvazXLe)
*   [
    
    ### Code Driven Animation
    
    ](https://codepen.io/creativeocean/pen/ByBogvj)
*   [
    
    ### Jello
    
    ](https://codepen.io/petebarr/pen/LYzBoeg)
*   [
    
    ### Alphabet Soup
    
    ](https://codepen.io/hexagoncircle/pen/ExoKBgW)
*   [
    
    ### The Police
    
    ](https://codepen.io/petebarr/pen/ZEYXrBK)
*   [
    
    ### GSAP ScrambleText on :hover/:focus
    
    ](https://codepen.io/jh3y/pen/mdNKWRb)
*   [
    
    ### 3D Rotation + SVG Filters
    
    ](https://codepen.io/cobra_winfrey/pen/vYNbJRB?editors=1010)

---

*This documentation was extracted from the database for URLs containing 'gsap'*
