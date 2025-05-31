# repeat | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Tween/repeat()](https://gsap.com/docs/v3/GSAP/Tween/repeat())  
**Last Updated:** 2025-05-23T00:24:33.639Z  
**Extracted:** 2025-05-31 16:56:03

---

# repeat | GSAP | Docs & Learning

### repeat( value:Number ) : \[Number | self\]

Gets or sets the number of times that the tween should repeat after its first iteration.

#### Parameters

*   #### **value**: Number
    
    (default = `0`) - Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.
    

### Returns : \[Number | self\][​](#returns--number--self "Direct link to returns--number--self")

Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.

### Details[​](#details "Direct link to Details")

Gets or sets the number of times that the tween should repeat after its first iteration. For example, if `repeat` is 1, the tween will play a total of twice (the initial play plus 1 repeat). To repeat indefinitely, use -1. `repeat` should always be an integer.

To cause the repeats to alternate between forward and backward, set `yoyo` to `true`. To add a time gap between repeats, use `repeatDelay`. You can set the initial repeat value via the `vars` parameter, like: `gsap.to(obj, {duration: 1, x: 100, repeat: 2});`

This method serves as both a getter and setter. Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining, like `myTween.repeat(2).yoyo(true).play();`

```
// Gets current repeatvar progress = myTween.repeat();// Sets repeat to 2myTween.repeat(2);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
