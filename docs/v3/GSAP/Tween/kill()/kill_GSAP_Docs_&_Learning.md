# kill | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Tween/kill()](https://gsap.com/docs/v3/GSAP/Tween/kill())  
**Last Updated:** 2025-05-23T00:23:54.343Z  
**Extracted:** 2025-05-31 16:56:03

---

# kill | GSAP | Docs & Learning

### kill( target:Object, propertiesList:String ) : self

Kills the animation entirely or in part depending on the parameters. To kill means to immediately stop the animation, remove it from its parent timeline, and release it for garbage collection.

#### Parameters

*   #### **target**: Object
    
    (default = `null`) - To kill only aspects of the animation related to a particular target (or targets), reference it here. For example, to kill only parts having to do with `myObject`, do `kill(myObject)` or to kill only parts having to do with `myObject1` and`myObject2`, do `kill([myObject1, myObject2])`. If no target is defined, **ALL** targets will be affected.
    
*   #### **propertiesList**: String
    
    (default = `"all"`) - a comma-delimited list of property names that should no longer be animated by this Tween. If no object (or `null` or `"all"`) is defined, **ALL** properties will be killed.
    

Kills the animation entirely or in part depending on the parameters. Simply calling `kill()` (omitting the parameters) will immediately stop the animation, remove it from its parent timeline, wipe out any property tweens and release it for garbage collection.

To kill only a certain target (or targets) from the animation, use the first parameter. To kill particular tweening properties of the animation, use the second parameter which is a comma-delimited list of property names.

```
// kill all parts of the animation related to the target "myObject" (if the tween has multiple targets, the others will not be affected):animation.kill(myObject);// kill only the "x" and "y" properties of the animation (all targets):animation.kill(null, "x,y");// kill only the "x" and "y" properties of animations of the target "myObject":animation.kill(myObject, "x,y");// kill only the "opacity" properties of animations of the targets "myObject1" and "myObject2":animation.kill([myObject1, myObject2], "opacity"); //you could use selector text instead, like ".class1, .class2"
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
