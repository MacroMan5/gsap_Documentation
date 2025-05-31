# formatNumber | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/HelperFunctions/helpers/formatNumber](https://gsap.com/docs/v3/HelperFunctions/helpers/formatNumber)  
**Last Updated:** 2025-05-23T00:20:13.841Z  
**Extracted:** 2025-05-31 16:56:03

---

# formatNumber | GSAP | Docs & Learning

## Format number with commas and limited decimal places

Take a number like 1000.254145 and format it into a string like "1,000.25".

```
// adds commas and forces 2 decimal places.function formatNumber(value, decimals) {  let s = (+value).toLocaleString("en-US").split(".");  return decimals    ? s[0] + "." + ((s[1] || "") + "00000000").substr(0, decimals)    : s[0];}
```

Then you can use it in an onUpdate:

```
let obj = { num: 100 };gsap.to(obj, {  num: 10500,  onUpdate: () => (myElement.innerText = "$" + formatNumber(obj.num, 2)),});
```

## getFormatter

I wasn't sure if you wanted to replace this file or create a new helper Jack? Thought as it's not urgent I would just partially do this so that you can give updating the docs a go?

```
function getFormatter(increment, pad) {  let snap = gsap.utils.snap(increment),      exp = /\B(?=(\d{3})+(?!\d))/g,      snapWithCommas = value => (snap(+value) + "").replace(exp, ","),      whole = increment % 1 === 0,      decimals = whole ? 0 : ((increment + "").split(".")[1] || "0").length;  return !pad || whole ? snapWithCommas : value => {    let s = snapWithCommas(value),        i = s.indexOf(".");    ~i || (i = s.length);    return s.substr(0, i) + "." + (s.substr(i + 1, s.length - i - 1) + "00000000").substr(0, decimals);  };}
```

```
let formatter = getFormatter(0.01, true); // increment by 0.01, always pad so that there are 2 decimal placesconsole.log(formatter(5000.1)); // 5,000.10
```

---

*This documentation was extracted from the database for URLs containing 'gsap'*
