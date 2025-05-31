# kill | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/Draggable/kill()](https://gsap.com/docs/v3/Plugins/Draggable/kill())  
**Last Updated:** 2025-05-23T00:29:11.607Z  
**Extracted:** 2025-05-31 16:56:03

---

# kill | GSAP | Docs & Learning

### kill( ) : Draggable

Disables the Draggable instance and removes it from the internal lookup table so that it is made eligible for garbage collection and it cannot be dragged anymore (unless `enable()` is called).

### Returns : Draggable[​](#returns--draggable "Direct link to Returns : Draggable")

The Draggable instance itself (to make chaining possible).

### Details[​](#details "Direct link to Details")

Disables the Draggable instance and removes it from the internal lookup table so that it is made eligible for garbage collection and it cannot be dragged anymore (unless `enable()` is called). `kill()` is identical to `disable()` except that the latter doesn't remove it from the internal lookup table, thus you could still use `Draggable.get("#yourID")` to find the associated Draggable instance after being disabled, but if you kill it, the `get()` method won't be able to find the Draggable anymore (necessary for garbage collection). If you don't plan to use the Draggable instance anymore, `kill()` it.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
