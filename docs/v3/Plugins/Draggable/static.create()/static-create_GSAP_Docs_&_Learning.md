# static-create | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/static.create()](https://gsap.com/docs/v3/Plugins/Draggable/static.create())  
**Last Updated:** 2025-05-23T00:28:32.155Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-create | GSAP | Docs & Learning

## Draggable.create

### Draggable.create( target:Object, vars:Object ) : Array

\[static\] A more flexible way to create Draggable instances than the constructor (`new Draggable(...)`).

#### Parameters

*   #### **target**: Object
    
    The element that should be draggable; this can be a regular DOM element or an array of elements. For example, `document.getElementById("yourID")` or `$("#yourID")` or `"#yourID"` or `[element1, element2, element3]`.
    
*   #### **vars**: Object
    
    An object containing optional configuration data like `{type: "x,y", inertia: true, edgeResistance: 0.8, onDrag: yourFunction}`.
    

### Returns : Array[​](#returns--array "Direct link to Returns : Array")

An array of Draggable instances (one for each element).

### Details[​](#details "Direct link to Details")

Provides a more flexible way to create Draggable instances than the constructor (`new Draggable(...)`) because the `Draggable.create()` method can accommodate elements, arrays of elements or even selector text like `".yourClass"`. `Draggable.create()` always returns an array of Draggable instances, one for each element. Remember an individual Draggable instance can only be associated with a single element - that's why `Draggable.create()` creates one for each element and spits back an array.

Any of the following are valid:

```
//a regular DOM elementDraggable.create(document.getElementById("yourID"), {type: "x,y"});//or selector textDraggable.create("#yourID", {type: "x,y"});//or an array of elementsDraggable.create([element1, element2, element3], {type: "x,y"});
```

The second parameter is the `vars` object that contains any optional configuration data. Any of the following properties can be defined:

## **Config Object**[​](#config-object "Direct link to config-object")

*   #### activeCursor[](#activeCursor)
    
    String - The cursor’s CSS value that should be used between the time they press and then release the pointer/mouse. This can be different than the regular `cursor` value, like: `cursor: "grab", activeCursor: "grabbing"`.
    
*   Boolean - If `true`, Draggable will allow context menus (like if a user right-clicks or long-touches). Normally this is suppressed because it can get in the way of dragging (especially on touch devices). Default: `false`.
    
*   #### allowEventDefault[](#allowEventDefault)
    
    Boolean - If `true`, `preventDefault()` won’t be called on the original mouse/pointer/touch event. This can be useful if you want to permit the default behavior like touch-scrolling. Typically, however, it’s best to let Draggable call `preventDefault()` on the events in order to deliver the best usability with dragging. Default: `false`.
    
*   #### allowNativeTouchScrolling[](#allowNativeTouchScrolling)
    
    Boolean - By default, allows you to native touch-scroll in the opposite direction as Draggables that are limited to one axis . For example, a Draggable of `type: "x"` or `"left"` would permit native touch-scrolling in the vertical direction, and `type: "y"` or `"top"` would permit native horizontal touch-scrolling. Default: `true`.
    
*   #### autoScroll[](#autoScroll)
    
    Number - To enable auto-scrolling when a Draggable is dragged within 40px of an edge of a scrollable container, set autoScroll to a non-zero value, where 1 is normal speed, 2 is double-speed, etc. (you can use any number). For a more intuitive or natural feel, it will scroll faster as the mouse/touch gets closer to the edge. The default value is 0 (no auto-scrolling). See [this CodePen](https://codepen.io/GreenSock/pen/YPvdYv/?editors=001) for a demo.
    
*   #### bounds[](#bounds)
    
    \[_Element_ | _String_ | _Object_\] - To cause the draggable element to stay within the bounds of another DOM element (like a container), you can pass the element like `bounds: document.getElementById("container")` or even selector text like `"#container"`. If you prefer, you can define bounds as a rectangle instead, like `bounds: {top: 100, left: 0, width: 1000, height: 800}` which is based on the parent’s coordinate system (top and left would be from the upper left corner of the parent). Or you can define specific maximum and minimum values like `bounds: {minX: 10, maxX: 300, minY: 50, maxY: 500}` or `bounds: {minRotation: 0, maxRotation: 270}`.
    
*   #### callbackScope[](#callbackScope)
    
    Object - The scope to be used for all of the callbacks (`onDrag`, `onDragEnd`, `onDragStart`, etc). The scope is what `this` refers to inside any of the callbacks. The older callback-specific scope properties are deprecated but still work.
    
*   #### clickableTest[](#clickableTest)
    
    Function - Your Draggable may contain child elements that are “clickable”, like links `<a>` tags, `<button/>` or `<input>` elements, etc. By default, it treats clicks and taps on those elements differently, not allowing the user to drag them. You can set `dragClickables: true` to override that, but it still may be handy to control exactly what Draggable considers to be a “clickable” element, so you can use your own function that accepts the clicked-on element as the only parameter and returns true or false accordingly. Draggable will call this function whenever the user presses their mouse or finger down on a Draggable, and the target of that event will be passed to your clickableTest function.
    
*   #### cursor[](#cursor)
    
    String - By default (except for `type: "rotation"`), the cursor CSS property of the element is set to `move` so that when the mouse rolls over it, there’s a visual cue indicating that it’s moveable, but you may define a different cursor if you prefer (as described at [https://devdocs.io/css/cursor](https://devdocs.io/css/cursor)) like `cursor: "pointer"`.
    
*   #### dragClickables[](#dragClickables)
    
    Boolean - By default, Draggable will work on pretty much any element, but sometimes you might want clicks on `<a>`, `<input>`, `<select>`, `<button>`, and `<textarea>` elements (as well as any element that has a `data-clickable="true"` attribute) NOT to trigger dragging so that the browser’s default behavior fires (like clicking on an input would give it focus and drop the cursor there to begin typing), so if you want Draggable to ignore those clicks and allow the default behavior instead, set `dragClickables: false`.
    
*   #### dragResistance[](#dragResistance)
    
    Number - A number between 0 and 1 that controls the degree to which resistance is constantly applied to the element as it is dragged, where 1 won’t allow it to be dragged at all, 0.75 applies a lot of resistance (making the object travel at quarter-speed), and 0.5 would be half-speed, etc. This can even apply to rotation.
    
*   #### edgeResistance[](#edgeResistance)
    
    Number - A number between 0 and 1 that controls the degree to which resistance is applied to the element as it goes outside the bounds (if any are applied), where 1 won’t allow it to be dragged past the bounds at all, 0.75 applies a lot of resistance (making the object travel at quarter-speed beyond the border while dragging), and 0.5 would be half-speed beyond the border, etc. This can even apply to rotation.
    
*   #### force3D[](#force3D)
    
    Boolean - By default, 3D transforms are used (when the browser supports them) in order to force the element onto its own layer on the GPU, thus speeding compositing. Typically this provides the best performance, but you can disable it by setting `force3D: false`. This may be a good idea if the element that you’re dragging contains child elements that are animating.
    
*   #### inertia[](#inertia)
    
    \[_Boolean_ | _Object_\] - InertiaPlugin is the key to getting the momentum-based motion after the users’ mouse (or touch) is released. To have Draggable auto-apply an InertiaPlugin tween to the element when the mouse is released (or touch ends), you can set `inertia: true` (`inertia` also works). Or for advanced effects, you can define the actual inertia object that will get fed into tween, like `inertia: {top: {min: 0, max: 1000, end: [0,200,400,600]}}`. However, if you want ultimate control over the InertiaPlugin tween, you can simply use an `onDragEnd` to call your own function that creates the tween. If `inertia: true` is defined, you may also use any of the following configuration properties that apply to the movement after the mouse/touch is released...
    
    View More details
    
    *   **snap** : \[_Function_ | _Object_ | _Array_\] - Allows you to define rules for where the element can land after it gets released. For example, maybe you want the rotation to always end at a 90-degree increment or you want the `x` and `y` values to be exactly on a grid (whichever cell is closest to the natural landing spot) or maybe you want it to land on a very specific value. You can define the snap in any of the following ways:
        *   **As a function** - This function will be passed one numeric parameter, the natural ending value. The function must return whatever the new ending value should be (you run whatever logic you want inside the function and spit back the value). For example, to make the value snap to the closest increment of 50, you’d do `snap: function(endValue) { return Math.round(endValue / 50) * 50; }`.
        *   **As an Array** - If you use an array of values, InertiaPlugin will first plot the natural landing position and then loop through the array and find the closest number (as long as it’s not outside any bounds you defined). For example, to have it choose the closest number from 10, 50, 200, and 450, you’d do `snap: [10,50,200,450]`.
        *   **As an object** - If you’d like to use different logic for each property, like if `type` is `"x,y"` and you’d like to have the `x` part snap to one set of values, and the `y` part snap to a different set of values, you can use an object that has matching properties, like: `snap:{x: [5,20,80,400], y: [10,60,80,500]}` or if `type` is `"top,left"` and you want to use a different function for each, you could do something like `snap: {top: function(endValue) { return Math.round(endValue / 50) * 50; }, left: function(endValue) { return Math.round(endValue / 100) * 100; }}`. You can define a points property inside this object that combines both `x` and `y`, like `liveSnap: {points: [{x: 0, y: 0},{x: 100, y: 0}], radius: 20}` which will snap to any point in the array when it’s within 20px (distance). Or you can even use a function-based value to run your own snapping logic, like `liveSnap: {points: function(point) { //run custom logic and return a new point }}`. See the [snapping section](#snapping) of this page for examples.
    *   **onThrowUpdate** : _Function_ - A function that should be called each time the InertiaPlugin tween updates/renders (basically on each “tick” of the engine while the tween is active). This only applies to the tween that gets generated after the user releases their mouse/touch - the function is not called while the user is dragging the element (that’s what `onDrag` is for). By default, the scope of the `onThrowUpdate` is the Draggable instance itself, but you may define an `callbackScope` if you prefer, just like any other tween.
    *   **onThrowComplete** : _Function_ - A function that should be called when the InertiaPlugin tween finishes. This only applies to the tween that gets generated after the user releases their mouse/touch - the function is not called immediately when the user releases their mouse/touch - that’s what `onDragEnd` is for. By default, the scope of the `onThrowComplete` is the Draggable instance itself, but you may define an `callbackScope` if you prefer, just like any other tween.
    *   **throwResistance** : _Number_ - A number (`1000` by default) that controls how much resistance or friction there is when the mouse/touch is released and momentum-based motion is enabled (by setting `inertia: true`). The larger the number, the more resistance and the quicker the motion decelerates. (requires InertiaPlugin and setting `inertia: true`, otherwise `throwResistance` will simply be ignored.)
    *   **maxDuration** : _Number_ - The maximum duration (in seconds) that the kinetic-based inertia tween can last. InertiaPlugin will automatically analyze the velocity and bounds and determine an appropriate duration (faster movements would typically result in longer tweens to decelerate), but you can cap the duration by defining a `maxDuration`. The default is 10 seconds. This has nothing to do with the maximum amount of time that the user can drag the object - it’s only the inertia tween that results after they release the mouse/touch. (requires InertiaPlugin and setting `inertia: true`, otherwise `maxDuration` will simply be ignored.)
    *   **minDuration** : _Number_ - The minimum duration (in seconds) that the kinetic-based inertia tween should last. InertiaPlugin will automatically analyze the velocity and bounds and determine an appropriate duration (faster movements would typically result in longer tweens to decelerate), but you can force the tween to take at least a certain amount of time by defining a `minDuration`. The default is 0.2 seconds. This has nothing to do with the minimum amount of time that the user can drag the object - it’s only the inertia tween that results after they release the mouse/touch. (requires InertiaPlugin and setting `inertia: true`, otherwise minDuration will simply be ignored.)
    *   **overshootTolerance** : _Number_ - Affects how much overshooting is allowed before smoothly returning to the resting position at the end of the tween. This can happen when the initial velocity from the flick would normally cause it to exceed the bounds/min/max. The larger the `overshootTolerance` the more leeway the tween has to temporarily shoot past the max/min if necessary. The default is `1`. If you don’t want to allow any overshooting, you can set it to `0`.
    
*   #### liveSnap[](#liveSnap)
    
    \[_Function_ | _Boolean_ | _Array_ | _Object_\] - Allows you to define rules that get applied **WHILE** the element is being dragged (whereas regular snap affects only the end value(s), where the element lands after the drag is released). For example, maybe you want the rotation to snap to 10-degree increments while dragging or you want the x and y values to snap to a grid (whichever cell is closest). You can define the `liveSnap` in any of the following ways:
    
    View More details
    
    *   **As a function** - This function will be passed one numeric parameter, the natural (unaltered) value. The function must return whatever the new value should be (you run whatever logic you want inside your function and spit back the value). For example, to make the value snap to the closest increment of 50, you’d do `liveSnap: function(value) { return Math.round(value / 50) * 50; }`.
    *   **As an array** - If you use an array of values, Draggable will loop through the array and find the closest number (as long as it’s not outside any bounds you defined). For example, to have it choose the closest number from 10, 50, 200, and 450, you’d do `liveSnap: [10,50,200,450]`.
    *   **As an object** - If you’d like to use different logic for each property, like if `type` is `"x,y"` and you’d like to have the “x” part snap to one set of values, and the “y” part snap to a different set of values, you can use an object that has matching properties, like: `liveSnap: {x: [5,20,80,400], y: [10,60,80,500]}`. Or if `type` is `"top,left"` and you want to use a different function for each, you’d do something like `liveSnap: {top: function(value) { return Math.round(value / 50) * 50; }, left: function(value) { return Math.round(value / 100) * 100; }}`. You can define a `points` property inside this object that combines both x and y, like `liveSnap: {points:[{x: 0, y: 0}, {x: 100, y: 0}], radius: 20}` which will snap to any point in the array when it’s within 20px (distance). Or you can even use a function-based value to run your own snapping logic, like `liveSnap: {points: function(point) { //run custom logic and return a new point }}`. See the [snapping section](#snapping) of this page for examples.
    *   **As a boolean (`true`)** - Live snapping will use whatever is defined for the `snap` (so that instead of only applying to the end value(s), it will apply it “live” while dragging too).
    
*   #### lockAxis[](#lockAxis)
    
    Boolean - If `true`, dragging more than 2 pixels in either direction (horizontally or vertically) will lock movement into that axis so that the element can only be dragged that direction (horizontally or vertically, whichever had the most initial movement) during that drag. No diagonal movement will be allowed. Obviously this is only applicable for Draggables with a `type` of `"x,y"`, or `"top,left"`. If you only want to allow vertical movement, you should set the `type` to `"y"` or `"top"`. If you only want to allow horizontal movement, you should set the `type` to `"x"` or `"left"`.
    
*   #### minimumMovement[](#minimumMovement)
    
    Number - By default, Draggable requires that the Draggable element moves more than 2 pixels in order to be interpreted as a drag, but you can change that threshold using `minimumMovement`. So `minimumMovement: 6` would require that the Draggable element moves more than 6 pixels to be interpreted as a drag.
    
*   #### onClick[](#onClick)
    
    Function - A function that should be called only when the mouse/touch is pressed on the element and released without moving 3 pixels or more. This makes it easier to discern the user’s intent (click or drag). Inside that function, `this` refers to the Draggable instance (unless you specifically set the scope using `callbackScope`), making it easy to access the target element (`this.target`) or the boundary coordinates (`this.maxX`, `this.minX`, `this.maxY`, and `this.minY`). By default, the `pointerEvent` (last mouse or touch event related to the Draggable) will be passed as the only parameter to the callback so that you can, for example, access its `pageX`, `pageY`, `target`, `currentTarget`, etc.
    
*   #### onClickParams[](#onClickParams)
    
    Array - An optional array of parameters to feed the `onClick` callback. For example, `onClickParams: ["clicked", 5]` would work with this code: `onClick: function(message, num) { console.log("message: " + message + ", num: " + num); }`.
    
*   #### onDrag[](#onDrag)
    
    Function - A function that should be called every time the mouse (or touch) moves during the drag. Inside that function, `this` refers to the Draggable instance (unless you specifically set the scope using `callbackScope`), making it easy to access the target element (`this.target`) or the boundary coordinates (`this.maxX`, `this.minX`, `this.maxY`, and `this.minY`). By default, the `pointerEvent` (last mouse or touch event related to the Draggable) will be passed as the only parameter to the callback so that you can, for example, access its `pageX`, `pageY`, `target`, `currentTarget`, etc. This is only called once per requestAnimationFrame.
    
*   #### onDragParams[](#onDragParams)
    
    Array - An optional array of parameters to feed the `onDrag` callback. For example, `onDragParams: ["dragged", 5]` would work with this code: `onDrag: function(message, num) { console.log("message: " + message + ", num: " + num); }`.
    
*   #### onDragEnd[](#onDragEnd)
    
    Function - A function that should be called as soon as the mouse (or touch) is **released** after the drag. Even if nothing is moved, the `onDragEnd` will always fire, whereas the `onClick` callback only fires if the mouse/touch moves is less than 3 pixels. Inside that function, `this` refers to the Draggable instance (unless you specifically set the scope using `callbackScope`), making it easy to access the target element (`this.target`) or the boundary coordinates (`this.maxX`, `this.minX`, `this.maxY`, and `this.minY`). By default, the `pointerEvent` (last mouse or touch event related to the Draggable) will be passed as the only parameter to the callback so that you can, for example, access `pageX`, `pageY`, `target`, `currentTarget`, etc.
    
*   #### onDragEndParams[](#onDragEndParams)
    
    Array - An optional array of parameters to feed the `onDragEnd` callback. For example, `onDragEndParams: ["drag ended", 5]` would work with this code: `onDragEnd: function(message, num) { console.log("message: " + message + ", num: " + num); }`.
    
*   #### onDragStart[](#onDragStart)
    
    Function - A function that should be called as soon as the mouse (or touch) moves more than 2 pixels, meaning that dragging has begun. Inside that function, `this` refers to the Draggable instance (unless you specifically set the scope using `callbackScope`), making it easy to access the target element (`this.target`) or the boundary coordinates (`this.maxX`, `this.minX`, `this.maxY`, and `this.minY`). By default, the `pointerEvent` (last mouse or touch event related to the Draggable) will be passed as the only parameter to the callback so that you can, for example, access `pageX`, `pageY`, `target`, `currentTarget`, etc.
    
*   #### onDragStartParams[](#onDragStartParams)
    
    Array - An optional array of parameters to feed the `onDragStart` callback. For example, `onDragStartParams: ["drag started", 5]` would work with this code: `onDragStart: function(message, num) { console.log("message: " + message + ", num: " + num); }`.
    
*   #### onLockAxis[](#onLockAxis)
    
    Function - A function that should be called as soon as movement is locked into the horizontal or vertical axis. This happens when `lockAxis` is `true` and the user drags enough for Draggable to determine which axis to lock. It also happens on touch-enabled devices when you have a Draggable whose type only permits it to drag along one axis (like `type: "x"`, `type: "y"`, `type: "left"`, or `type: "top"`) and the user touch-drags and Draggable determines the direction, either allowing native touch-scrolling or Draggable-induced dragging. Inside the function, `this` refers to the Draggable instance, making it easy to access the locked axis (`this.lockedAxis` which will either be `"x"` or `"y"`), or the target element (`this.target`), etc. By default, the `pointerEvent` (last mouse or touch event related to the Draggable) will be passed as the only parameter to the callback so that you can, for example, access `pageX`, `pageY`, `target`, `currentTarget`, etc.
    
*   #### onMove[](#onMove)
    
    Function - A function that should be called every time the mouse (or touch) moves during the drag. Inside that function, `this` refers to the Draggable instance (unless you specifically set the scope using `callbackScope`), making it easy to access the target element (`this.target`) or the boundary coordinates (`this.maxX`, `this.minX`, `this.maxY`, and `this.minY`). By default, the `pointerEvent` (last mouse or touch event related to the Draggable) will be passed as the only parameter to the callback so that you can, for example, access its `pageX`, `pageY`, `target`, `currentTarget`, etc. This is different than `onDrag` in that it can fire multiple times per requestAnimationFrame. In general, it is better to use `onDrag`, but this is available if, for some reason, need to `.stopPropogation` or `.stopImmediatePropogation` on the drag event.
    
*   #### onPress[](#onPress)
    
    Function - A function that should be called as soon as the mouse (or touch) presses down on the element. Inside that function, `this` refers to the Draggable instance (unless you specifically set the scope using `callbackScope`), making it easy to access the target element (`this.target`) or the boundary coordinates (`this.maxX`, `this.minX`, `this.maxY`, and `this.minY`). By default, the `pointerEvent` (last mouse or touch event related to the Draggable) will be passed as the only parameter to the callback so that you can, for example, access `pageX`, `pageY`, `target`, `currentTarget`, etc.
    
*   #### onPressInit[](#onPressInit)
    
    Function - A function that should be called before the starting values are recorded in the `onPress`, allowing you to make changes before any dragging occurs. `onPressInit` always fires BEFORE `onPress`. [See demo](https://codepen.io/GreenSock/pen/62fd4014cf86a9a87e632c8b4f967ed4/?editors=0010).
    
*   #### onPressParams[](#onPressParams)
    
    Array - An optional array of parameters to feed the `onPress` callback. For example, `onPressParams: ["drag started", 5]` would work with this code: `onPress: function(message, num) { console.log("message: " + message + ", num: " + num); }`.
    
*   #### onRelease[](#onRelease)
    
    Function - A function that should be called as soon as the mouse (or touch) is released after having been pressed on the target element, regardless of whether or not anything was dragged. Inside that function, `this` refers to the Draggable instance (unless you specifically set the scope using `callbackScope`), making it easy to access the target element (`this.target`) or the boundary coordinates (`this.maxX`, `this.minX`, `this.maxY`, and `this.minY`). By default, the `pointerEvent` (last mouse or touch event related to the Draggable) will be passed as the only parameter to the callback so that you can, for example, access `pageX`, `pageY`, `target`, `currentTarget`, etc.
    
*   #### onReleaseParams[](#onReleaseParams)
    
    Array - An optional array of parameters to feed the `onRelease` callback. For example, `onReleaseParams: ["drag ended", 5]` would work with this code: `onRelease: function(message, num) { console.log("message: " + message + ", num: " + num); }`.
    
*   #### trigger[](#trigger)
    
    \[_Element_ | _String_ | _Object_\] - If you want only a certain area to trigger the dragging (like the top bar of a window) instead of the entire element, you can define a child element as the trigger, like `trigger: yourElement`, `trigger: "#topBar"`, or `trigger: $("#yourID")`. You may define the trigger as an element or a selector string
    
*   #### type[](#type)
    
    String - Indicates the type of dragging (the properties that the dragging should affect). Any of the following work: \[`"x,y"` (basically the `translateX` and `translateY` of transform) | `"left,top"` | `"rotation"` |`"x"` | `"y"` | `"top"` | `"left"`\]. The default is `"x,y"`.
    
*   #### zIndexBoost[](#zIndexBoost)
    
    Boolean - By default, for vertical or horizontal dragging, when an element is pressed/touched, it has its `zIndex` set to a high value (`1000` by default) and that number gets incremented and applied to each new element that gets pressed/touched so that the stacking order looks correct (newly pressed objects rise to the top), but if you prefer to skip this behavior set `zIndexBoost: false`.
    

Note that if you're applying Draggable to a dynamically created element, that element should first be appended to the DOM before calling Draggable.create().

---

*This documentation was extracted from the database for URLs containing 'gsap'*
