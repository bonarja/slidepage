# SlidePage

Slidepage is a simple complement in pure javascript that allows you to create sliding views in a container, provides functions to control this, returning promises.

## Use Example

```html
<div class="app">
    <div class="sp_page">Page 1</div>
    <div class="sp_page">Page 2</div>
    <div class="sp_page">Page 3</div>
</div>
<button onclick="sp.prev()">PREV</button>
<button onclick="sp.next()">NEXT</button>
```

```javascript
var sp = new SLIDEPAGE({
    el: ".app",
    repeat: true, // default: false
    realNumber: true, // default: false
    direction: "x", // default: x
    display: "block", // default: block
    transition: 300, // default: 250
    forceDirection: true // default: true
});
```

## Options

-   `el`: containt, allows name or DOM element
-   `repeat`: repetitive or circular slide
-   `realNumber`: start indexing from 1
-   `direction`: slide direction, x from horizontal, y from vertical
-   `display`: select the method to show each page (block, flex, etc)
-   `transition`: duration of the animation in ms
-   `forceDirection`: continue the same direction of the slide when you reach the end when reapeat is true

## Methods

all methods are promises, these are fulfilled when the animation is complete, except the show function.

-   `go`: take the slider to a page, recive the number of this
-   `next`: go to the next page
-   `prev`: go to the previous page
-   `show`: take the slider to a page, recive the number of this (without animation, no promise)

### Note:

the promises function (go, next, prev) returns object with `{current, previous}` pages, the function show (no promise) return an object `{current, previous}` pages

## Promises

```javascript
var sp = new SLIDEPAGE({
    el: ".app"
});
sp.go(1).then(data => {
    console.log("the animation has been completed");
    console.log("the current page:", data.current);
    console.log("the preious page:", data.previous);
});
```
