# static-stringToRawPath | GSAP | Docs & Learning

**Source URL:** [https://gsap.com/docs/v3/Plugins/MorphSVGPlugin/static.stringToRawPath](https://gsap.com/docs/v3/Plugins/MorphSVGPlugin/static.stringToRawPath)  
**Last Updated:** 2025-05-23T00:31:07.562Z  
**Extracted:** 2025-05-31 16:56:03

---

# static-stringToRawPath | GSAP | Docs & Learning

## MorphSVGPlugin.stringToRawPath

### MorphSVGPlugin.stringToRawPath( data:String ) : RawPath

Takes a string of path data (like `"M0,0 C100,20 300,50 400,0..."`, what's typically found in the `d` attribute of a `<path>`), parses it, converts it into cubic beziers, and returns it as a RawPath which is just an array containing an array for each segment (each `M` command starts a new segment).

#### Parameters

*   #### **data**: String
    
    A path data string which is what is typically found in the `d` attribute of a `<path>` element. Like `"M0,0 C10,20,15,30,5,18 M0,100 C50,120,80,110,100,100"`.
    

### Returns : RawPath[​](#returns--rawpath "Direct link to Returns : RawPath")

The RawPath of a given string, like

```
[  [0, 0, 10, 20, 15, 30, 5, 18],  [0, 100, 50, 120, 80, 110, 100, 100],];
```

### Details[​](#details "Direct link to Details")

Converts a string of path data, like `"M0,0 C100,20 300,50 400,0..."` (which is what's typically found in the `d` attribute of a `<path>`) into a **RawPath**.

A **RawPath** is essentially an array containing an array for each contiguous segment with alternating x, y, x, y cubic bezier data. It's like an SVG `<path>` where there's one segment (array) for each `M` command. That segment (array) contains all of the cubic bezier coordinates in alternating x/y format (just like SVG path data) in raw numeric form which is nice because that way you don't have to parse a long string and convert things.

For example, this SVG `<path>` has two separate segments because there are two "M" commands:

```
<path d="M0,0 C10,20,15,30,5,18 M0,100 C50,120,80,110,100,100" />
```

The resulting RawPath would be:

```
[  [0, 0, 10, 20, 15, 30, 5, 18],  [0, 100, 50, 120, 80, 110, 100, 100],];
```

For simplicity, the example above only has one cubic bezier in each segment, but there could be an unlimited quantity inside each segment. No matter what path commands are in the original`<path>` data string (cubic, quadratic, arc, lines, whatever), the resulting RawPath will **ALWAYS** be cubic beziers.

There is also a corresponding `MorphSVGPlugin.rawPathToString()` method so that you can convert back and forth.

---

*This documentation was extracted from the database for URLs containing 'gsap'*
