# static-hitTest | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/static.hitTest()](https://gsap.com/docs/v3/Plugins/Draggable/static.hitTest())  
**Last Updated:** 2025-05-23T00:29:05.322Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-hitTest | GSAP | Docs & Learning

```
<main>
  <svg class="logo" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 623 231">
    
    <linearGradient id="gradient" gradientTransform="rotate(-25)">
      <stop offset="0%" stop-color="rgb(255, 252, 225)" />
      <stop offset="70%" stop-color="rgb(255, 252, 225)" />
    </linearGradient>

    <path fill="url(#gradient)" d="m182 108-8 36c-1 2-3 3-5 3h-10l-2 2c-9 31-21 52-37 65a82 82 0 0 1-54 16c-21 0-35-6-47-19-15-18-21-46-18-81C8 66 42 1 105 1c20 0 35 6 46 18s16 32 16 57c0 2-1 4-4 4h-46c-2 0-4-2-4-3 0-18-5-26-15-26-18 0-29 24-34 38-8 19-12 40-11 60 0 10 2 23 11 29 8 5 19 2 26-4 7-5 12-15 15-23v-3l-2-1H91l-4-1v-3l8-36c0-2 2-3 4-3h79c2 0 4 2 4 4Z M317 67c0 2-2 4-4 4h-43c-3 0-5-3-5-5 0-13-4-19-13-19s-15 5-15 15c0 11 6 20 23 37 22 21 31 40 31 65-1 41-28 67-69 67-22 0-38-6-48-17-11-11-16-28-15-50 0-2 2-4 4-4h44l4 2v3c0 7 1 13 4 16 2 3 5 4 8 4 9 0 13-6 14-16 0-9-3-17-18-33-20-19-37-39-36-70 0-18 7-35 20-47s31-19 52-19c22 0 38 6 48 18 10 11 15 28 14 49Zm134 156V8a4 4 0 0 0-4-4h-67c-2 0-3 2-4 3l-96 215c-1 3 1 6 4 6h46c3 0 4-1 5-3l10-22c1-3 1-3 4-3h45c3 0 3 0 3 3l-1 21a4 4 0 0 0 4 4h47l3-2a4 4 0 0 0 1-3Zm-83-71h-1a1 1 0 0 1-1-2l1-1 33-83 1-3h1l-3 85c-1 4-1 4-4 4h-27ZM545 4h-35c-2 0-4 1-4 3l-50 216a3 3 0 0 0 1 3l3 2h45c2 0 4-2 4-4l5-24c1-2 0-3-2-4l-2-2-8-4-7-4-3-1a1 1 0 0 1-1-1 2 2 0 0 1 2-2h24c7 0 14 0 21-2 51-9 84-50 85-105 1-47-25-71-77-71h-1Zm-12 129h-1l-2-1 14-62-1-3-22-12a1 1 0 0 1 0-1 2 2 0 0 1 1-2h32c10 0 16 10 16 25-1 27-13 55-37 56Zm48 95c8 0 13-6 13-13 0-8-5-14-13-14-7 0-13 6-13 14 0 7 6 13 13 13Zm-10-14c0-6 4-10 10-10s10 4 10 10c0 7-3 11-10 11s-10-4-10-11Zm5 7h4v-5h1c3 0 2 5 3 5h4c-1 0 0-6-3-6 1-1 3-2 3-4s-2-4-6-4h-6v14Zm4-8v-3h1c2 0 2 0 2 2l-2 1h-1Z"/>
    
  </svg>
  
  <div class="img-group">
    <p>( drag over logo to change color )</p>
    <img alt="" src="https://assets.codepen.io/16327/flair-11.png"/>
    <img alt="" src="https://assets.codepen.io/16327/flair-3.png"/>
    <img alt="" src="https://assets.codepen.io/16327/flair-2.png"/>
    <img alt="" src="https://assets.codepen.io/16327/flair-17.png"/>    
  </div>
</main>
```

```
@font-face {
  font-display: block;
  font-family: Mori;
  font-style: normal;
  font-weight: 400;
  src: url(https://assets.codepen.io/16327/PPMori-Regular.woff) format("woff");
}

html, body {
  margin:0;
  padding:0;
  font-family: "Mori";
  color:rgb(255, 252, 225);
  background: #0e100f;
}

body{
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  min-height:100vh;
}

main {
  width:100%;
  height:100vh;
  max-height:100vw;
  display:flex;
  align-items:center;
  justify-content:center;  
  flex-direction:column;
}

svg.logo {
  width:40%;
  max-width:600px;
}

.img-group {
  text-align:center;
  margin-top: 3rem;
}

.img-group img {
  position:relative;
  width:20%;
  margin:2%;
  max-width:150px;
}
```

```
gsap.registerPlugin(Draggable);

const colors = [
  ["rgb(155, 237, 255)","rgb(3, 127, 154)"],
  ["rgb(10, 228, 72)","rgb(171, 255, 132)"],
  ["rgb(255, 135, 9)","rgb(247, 189, 248)"],
  ["rgb(241, 0, 203)","rgb(254, 197, 251)"]
]

const logo = document.querySelectorAll('.logo')
const imgGroup = document.querySelector('.img-group')
const items = document.querySelectorAll('.img-group img')

items.forEach((item,i)=>{
  
  const itemColor = colors[i]
  
  Draggable.create(item, {
    onPress:()=>{ // bring the item forward on press
      gsap.to(item, {duration:0.1, scale:1.2, rotate:'random(-9,9)', zIndex:100})
      gsap.to(items, {duration:0.1, opacity:(i,t)=>(t==item)?1:0.3})
    },
    
    onRelease:()=>{ // return the item on release
      gsap.to(item, {duration:0.4, x:0, y:0, rotate:0, scale:1, ease:'elastic.out(.45)'})
      gsap.to(items, {duration:0.2, opacity:1, zIndex:0 })
    },
    
    onDrag:()=>{
      if ( !gsap.isTweening(logo) ){ // prevent overlapping color changes
        if ( Draggable.hitTest(item, logo, 12) ){ // check if item is over the logo
          gsap.to('.logo #gradient stop', { // if so, change stop element's stop-color attribute
            attr:{ 'stop-color' : (n) => itemColor[n] }
          })
        }
      }
    }
  })
  
})


// // 💚 This just adds the GSAP link to this pen, don't copy this bit
// import { GSAPInfoBar } from "https://codepen.io/GreenSock/pen/vYqpyLg.js"
// new GSAPInfoBar({ link: "https://gsap.com/docs/v3/Plugins/Draggable/" });
// // 💚 Happy tweening!
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
