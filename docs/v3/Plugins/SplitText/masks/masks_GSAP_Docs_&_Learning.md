# masks | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/SplitText/masks](https://gsap.com/docs/v3/Plugins/SplitText/masks)  
**Last Updated:** 2025-05-23T00:34:50.009Z  
**Extracted:** 2025-05-31 16:56:03

---

# masks | GSAP | Docs & Learning

### masks : Array<Element>

Wrapper elements created when using `mask: "lines"`, `"words"` or `"chars"`.

### Details[​](#details "Direct link to Details")

An array containing all of the wrapper elements created by the `mask` feature. When you use `mask: "lines"`, `"words"`, or `"chars"`, SplitText wraps each corresponding part in an extra `<div>` with `overflow: clip`, allowing for simple masked reveal animations. Access them in a "masks" Array on the SplitText instance. If you set a class name for the `lines/words/chars`, it'll append `"-mask"` for easy selecting.

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

---

*This documentation was extracted from the database for URLs containing 'gsap'*
