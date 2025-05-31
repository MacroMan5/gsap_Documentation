# getDirection | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/getDirection()](https://gsap.com/docs/v3/Plugins/Draggable/getDirection())  
**Last Updated:** 2025-05-23T00:29:00.014Z  
**Extracted:** 2025-05-31 16:56:03

---

# getDirection | GSAP | Docs & Learning

```
<h1>Draggable with direction sensing</h1>
<div class="dataDisplay">this.getDirection(<strong>"start"</strong>): <span id="directionStart">-</span></div>
<div class="dataDisplay">this.getDirection(<strong>"velocity"</strong>): <span id="directionVelocity">-</span></div>
<div class="dataDisplay">this.getDirection(<strong>logoElement</strong>): <span id="directionObject">-</span></div>
<div id="container">
<img src="https://assets.codepen.io/16327/gsap-logo-green.svg" id="logoElement" width="150"/>
    <div class="box" id="original">Start position</div>
    <div class="box gradient-green" id="box1">Drag me</div>
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
body {
  padding: 14px;
}

h1 {
  font-weight: 400;
  margin: 0 0 5px 0;
}

.dataDisplay {
  font-size: 20px;
  font-weight: 300;
  font-family: monospace;
  margin: 10px 0;
}

p span {
  font-weight: 400;
}

#container {
  height: 440px;
  width: 90%;
  overflow: visible;
  padding: 0;
  position: relative;
  border-radius: 10px;
  border: 2px dashed var(--color-surface-white);
}

.box {
  text-align: center;
  width: 196px;
  height: 100px;
  line-height: 100px;
  color: black;
  position: absolute;
  top: 0;
  font-size: 18px;
  -webkit-border-radius: 10px;
  -moz-border-radius: 10px;
  border-radius: 10px;
}
a,
a:hover,
a:visited {
  color: #71b200;
}

#logoElement {
  position: absolute;
  left: 50%;
  top: 50%;
}

.dataDisplay strong {
  color: #d0782a;
  font-weight: 400;
}

#directionStart,
#directionVelocity,
#directionObject {
  color: #91e600;
  font-weight: 400;
}

#original {
  background-color: transparent;
  box-sizing: border-box;
  border: solid 2px var(--color-surface-white);
  color: var(--color-surface-white);
}
```

```
/*
This demo illustrates direction sensing capabilities in Draggable

Watch a video explaining all the details: https://greensock.com/gsap-1-16

The getDirection() method can determine
 - direction from where the drag started
 - momementary direction 
 - direction relative to any elment

*/
var directionStart = document.getElementById("directionStart"),
    directionVelocity = document.getElementById("directionVelocity"),
    directionObject = document.getElementById("directionObject"),
    original = document.getElementById("original"),
    logoElement = document.getElementById("logoElement");

Draggable.create("#box1", {
  bounds:"#container",
  edgeResistance:0.65,
  inertia:true,
  autoScroll:1,
  onDrag:updateDirections,
  onThrowUpdate:updateDirections,
  onThrowComplete:function() {
    //move the original marker to end position
    gsap.to(original, {duration:1, x:this.x, y:this.y});
  }
});

function updateDirections() {
    //getDirection() can return 3 types of direction...
    directionStart.innerHTML = '"' + this.getDirection("start") + '"'; //direction from start of drag
    directionVelocity.innerHTML = '"' + this.getDirection("velocity") + '"'; //momentary velocity *requires InertiaPlugin
    directionObject.innerHTML = '"' + this.getDirection(logoElement) + '"'; //direction from an object
}

gsap.set(logoElement, {xPercent:-50, yPercent:-50})

/*
See https://www.greensock.com/draggable/ for details about Draggable. 
This demo uses InertiaPlugin which is a membership benefit of Club GreenSock, https://www.greensock.com/club/
InertiaPlugin is necessary for getDirection("velocity").
*/
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
