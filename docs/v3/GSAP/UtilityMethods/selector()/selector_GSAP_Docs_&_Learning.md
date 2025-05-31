# selector | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/UtilityMethods/selector()](https://gsap.com/docs/v3/GSAP/UtilityMethods/selector())  
**Last Updated:** 2025-05-23T00:16:00.728Z  
**Extracted:** 2025-05-31 16:56:03

---

# selector | GSAP | Docs & Learning

### Returns : Function[​](#returns--function "Direct link to Returns : Function")

* * *

Returns a **selector function** that's scoped to a particular Element, meaning it'll only find **descendants** of that Element.

This is great for components because you can create a scoped selector for that component's main container element and then use that to select descendants. It's similar to calling `.querySelectorAll()` on that element – rather than on the document – except with a few added benefits:

*   It returns an **[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)** rather than a [NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList), so you get access to convenient array methods like `.filter()` and `.map()`.
*   You can pass a [React ref](https://reactjs.org/docs/refs-and-the-dom.html) or [Angular ElementRef](https://angular.io/api/core/ElementRef) to [gsap.utils.selector()](https://gsap.com/docs/v3/GSAP/UtilityMethods/selector\(\)). Then when you use the resulting function, it will automatically check for the `.current`/`.nativeElement` in case it was re-rendered since creation.

```
// Vanillalet q = gsap.utils.selector(myElement); // or use selector text like ".class"let boxes = q(".box"); // finds only elements with the class "box" that are INSIDE myElement// or plug directly into animationsgsap.to(q(".circle"), { x: 100 });
```

```
// Reactlet el = useRef();let q = gsap.utils.selector(el);useEffect(() => {  // uses el.current.querySelectorAll() internally  gsap.to(q(".box"), { x: 100 });}, []);
```

```
// Angular@Component({ ... })class MyComponent implements OnInit {  constructor(private el: ElementRef) {    this.q = gsap.utils.selector(el);  }  ngOnInit() {    // uses this.el.nativeElement.querySelectorAll() internally    gsap.to(this.q(".box"), { x: 100 });  }}
```

```
// Vue{  mounted() {    this.$nextTick(() => this.animate());  },  methods: {    animate() {      let q = gsap.utils.selector(this.$el);      // uses this.$el.querySelectorAll() internally      gsap.to(q(".box"), { x: 100 });    }  }}
```

A common pattern in React is to declare a ref for every element you want to animate, but that can make your code very verbose and hard to read.

#### loading...

  CodePen Embed - React forwarding refs  

```
@import url('https://fonts.googleapis.com/css2?family=Signika+Negative:wght@400;600&display=swap');

body {
  font-family: "Signika Negative", sans-serif, Arial;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  overflow: hidden;
    background-color: #28292b;
  color: #fffce1;
}

h1 {
  text-align: center;
  font-weight: 400;
}

#app {
  display: flex;
  justify-content: center;
}

.box {
  width: 80px;
  height: 80px;
  background: dodgerblue;
  margin: 10px;
  float: left;
  opacity: 0;
  border-radius: 6px;
  transform: scale(0.3);
}
```

```
let { useRef, useEffect, forwardRef } = React;

let data = [
  { id: 0 },
  { id: 1 },
  { id: 2 },
  { id: 3 },
  { id: 4 }
];

// To get a ref from a child component, we must forward
// the ref up to the parent
let Box = forwardRef((props, ref) => {
  return <div className="box" ref={ref}></div>
});

let App = () => {
  let boxRefs = useRef([]);
  
  useEffect(() => {
    gsap.to(boxRefs.current, {
      opacity: 1,
      scale: 1,
      duration: 1,
      stagger: 0.1,
      repeat: -1,
      repeatDelay: 1,
      yoyo: true
    });
  }, []);
  
  return (
    <div>
      <h1>React forwarding refs</h1>
      {data.map((item, i) => <Box key={item.id} ref={e => boxRefs.current[i] = e} />)}
    </div>
  );
}

ReactDOM.render(<App/>, document.querySelector('#app'));
```

[View Compiled](#0)

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

By using a scoped selector, we only need to use a **single** ref. Then we can simply select the descendants.

#### loading...

  CodePen Embed - React scoped selector  

```
@import url('https://fonts.googleapis.com/css2?family=Signika+Negative:wght@400;600&display=swap');

body {
  font-family: "Signika Negative", sans-serif, Arial;
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  overflow: hidden;
  background-color: #28292b;
  color: #fffce1;
}

h1 {
  text-align: center;
  font-weight: 400;
}

#app {
  display: flex;
  justify-content: center;
}

.box {
  width: 80px;
  height: 80px;
  background: dodgerblue;
  margin: 10px;
  float: left;
  opacity: 0;
  border-radius: 6px;
  transform: scale(0.3);
}
```

```
let { useRef, useEffect } = React;

let data = [
  { id: 0 },
  { id: 1 },
  { id: 2 },
  { id: 3 },
  { id: 4 }
];

let Box = () => {
  return <div className="box"></div>
};

let App = () => {
  let el = useRef();
  let q = gsap.utils.selector(el);
  
  useEffect(() => {
    
    // The component has been rendered, so we can now select
    // descendants of the component, including descendants
    // nested inside of other components    
    gsap.to(q(".box"), {
      opacity: 1,
      scale: 1,
      duration: 1,
      stagger: 0.1,
      repeat: -1,
      repeatDelay: 1,
      yoyo: true
    });
  }, []);
  
  return (
    <div ref={el}>
      <h1>React scoped selector</h1>
      {data.map((item) => <Box key={item.id} />)}
    </div>
  );
}

ReactDOM.render(<App/>, document.querySelector('#app'));
```

[View Compiled](#0)

[![](https://assets.codepen.io/16327/internal/avatars/users/default.png?fit=crop&format=auto&height=256&version=1697554632&width=256)](https://codepen.io/GreenSock)

## Why not just use document.querySelectorAll(".class")?[​](#why-not-just-use-documentqueryselectorallclass "Direct link to Why not just use document.querySelectorAll(\".class\")?")

Let's say you build a component that ends up rendering on a page like:

```
<div class="my-component">  <div class="box"></div>  <div class="box"></div>  <div class="box"></div></div>
```

And then you use that component 3 times on a page...

```
<my-component><my-component><my-component>
```

Which then renders like:

```
<div class="my-component">  <div class="box"></div>  <div class="box"></div>  <div class="box"></div></div><div class="my-component">  <div class="box"></div>  <div class="box"></div>  <div class="box"></div></div><div class="my-component">  <div class="box"></div>  <div class="box"></div>  <div class="box"></div></div>
```

Now think about what would happen if you wrote an animation like this so that when you click on an individual component, it animates its boxes:

```
myComponent.addEventListener("click", () =>  gsap.to(".my-component .box", { x: 100, stagger: 0.1 }));
```

That would end up making **ALL** the boxes on the entire page animate instead of just the ones inside that component. See the issue? We need a way to scope it to just the one component. Of course you could do `myComponentRef.current.querySelectorAll(".box")` as your tween's target but it just seems cleaner to have a selector() that's already scoped and you can just reuse that over and over again to select things by class name (but only in that component).

## Parameters[​](#parameters "Direct link to Parameters")

1.  **scope** : \[Element | String | Object\] (optional) - The Element (or selector text or React Ref or Angular ElementRef) to which the selector text scope should be limited, like calling `scopeElement.querySelectorAll([selector-text])` rather than `document.querySelectorAll()`. In other words, it will only return **descendant** Elements of the scope Element. Remember, `gsap.utils.selector()` returns a reusable **selector function**, not the results of the selection.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
