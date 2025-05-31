# resume | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/GSAP/Tween/resume()](https://gsap.com/docs/v3/GSAP/Tween/resume())  
**Last Updated:** 2025-05-23T00:23:37.430Z  
**Extracted:** 2025-05-31 16:56:03

---

# resume | GSAP | Docs & Learning

### resume( ) : self

Resumes playing without altering direction (forward or reversed).

### Returns : self[​](#returns--self "Direct link to Returns : self")

For easier chaining

### Details[​](#details "Direct link to Details")

Resumes playing without altering direction (forward or reversed).

**Note:** if the Tween's timeScale is exactly 0 when resume() is called, it will be changed to 1 (otherwise it wouldn't play). If you're going to tween it up from 0 you can set it to a very small number before calling resume() like `myAnimation.timeScale(myAnimation.timeScale() || 0.001).resume()` so that it doesn't jump to 1.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
