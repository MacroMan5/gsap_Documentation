# shiftChildren | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Timeline/shiftChildren()](https://gsap.com/docs/v3/GSAP/Timeline/shiftChildren())  
**Last Updated:** 2025-05-23T00:26:59.714Z  
**Extracted:** 2025-05-31 16:56:03

---

# shiftChildren | GSAP | Docs & Learning

### shiftChildren( amount:Number, adjustLabels:Boolean, ignoreBeforeTime:Number ) : self

Shifts the startTime of the timeline's children by a certain amount and optionally adjusts labels too.

#### Parameters

*   #### **amount**: Number
    
    Number of seconds (or frames for frames-based timelines) to move each child.
    
*   #### **adjustLabels**: Boolean
    
    (default = `false`) - If `true`, the timing of all labels will be adjusted as well.
    
*   #### **ignoreBeforeTime**: Number
    
    (default = `0`) - All children that begin at or after the `startAtTime` will be affected by the shift (the default is 0, causing all children to be affected). This provides an easy way to splice children into a certain spot on the timeline, pushing only the children after that point back to make room.
    

### Returns : self[​](#returns--self "Direct link to Returns : self")

self (makes chaining easier)

### Details[​](#details "Direct link to Details")

Shifts the `startTime` of the timeline's children by a certain amount and optionally adjusts labels too. This can be useful when you want to prepend children or splice them into a certain spot, moving existing ones back to make room for the new ones.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
