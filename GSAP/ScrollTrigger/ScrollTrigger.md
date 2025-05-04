
# 🧲 ScrollTrigger Animations with GSAP

This section demonstrates scroll-based animations using [GSAP ScrollTrigger](https://gsap.com/docs/v3/Plugins/ScrollTrigger/). ScrollTrigger lets you trigger animations when elements enter or leave the viewport, pin elements, and sync animations with scroll position.


## 📦 What is ScrollTrigger?

**ScrollTrigger** is a GSAP plugin that enables scroll-driven animations. It allows you to:

- Animate elements as they enter/leave the viewport
- Pin elements while scrolling
- Synchronize animations with scroll progress
- Create parallax effects
### 🔧 Basic Usage Example:
HTML
```html
    <div class="div1"></div>
    <div class="div2">
      <div class="square"></div>
      <div class="square2"></>
    </div>
```
CSS
```css
    .div1, .div2 {
        height: 100vh;
    }

    .div1 {
        background-color: pink;
    }

    .div2 {
        background-color: salmon;
    }

    .square,
    .square2 {
        width: 150px;
        height: 150px;
        border-radius: 10px;
    }

    .square {
        background-color: blue;
    }

    .square2 {
        margin-top: 200px;
        background-color: yellow;
    }
```
JavaScript

- You activate the ***ScrollTrigger*** plugin
```js
gsap.registerPlugin(ScrollTrigger);
```
- First animation: for `.square` box
```js
gsap.to(".square", {
  x: 700,
  duration: 3,
  scrollTrigger: ".square",
});
```

> What does this mean?

> `.square` moves 700px to the right

> This move should happen in 3 seconds

> But not immediately — only when `.square` appears into viewport

> So: "blue box (.square) enters the viewport → start moving right"

- Second animation: again for `.square` but with trigger `.square2`

```js
gsap.to(".square", {
  x: 700,
  duration: 3,
  scrollTrigger: ".square2",
});
```
> What does this mean?

> Here everything is the same as before, but this time the trigger is `.square2`

> So "when you see a yellow box (.square2), the blue box (.square2) should move to the right"


