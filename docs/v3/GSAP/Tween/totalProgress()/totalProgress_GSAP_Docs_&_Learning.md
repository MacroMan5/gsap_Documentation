# totalProgress | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Tween/totalProgress()](https://gsap.com/docs/v3/GSAP/Tween/totalProgress())  
**Last Updated:** 2025-05-23T00:25:02.409Z  
**Extracted:** 2025-05-31 16:56:03

---

# totalProgress | GSAP | Docs & Learning

### totalProgress( value:Number, suppressEvents:Boolean ) : \[Number | self\]

\[override\] Gets or sets the tween's totalProgress which is a value between 0 and 1 indicating the position of the virtual playhead (including repeats) where 0 is at the beginning, 0.5 is halfway complete, and 1 is complete.

#### Parameters

*   #### **value**: Number
    
    (default = `NaN`) - Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.
    
*   #### **suppressEvents**: Boolean
    
    (default = `false`) - If `true`, no events or callbacks will be triggered when the playhead moves to the new position.
    

Omitting the parameter returns the current value (getter), whereas defining the parameter sets the value (setter) and returns the instance itself for easier chaining.

Gets or sets the tween's totalProgress which is a value between 0 and 1 indicating the position of the virtual playhead (**including repeats**) where 0 is at the beginning, 0.5 is halfway complete, and 1 is complete.

```
//gets current total progressvar progress = myTween.totalProgress();//sets total progress to one quarter finishedmyTween.totalProgress(0.25);
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
