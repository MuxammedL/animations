
# 📍 ScrollTrigger: `start` and `end`
GSAP’s ScrollTrigger gives you full control over when an animation begins and ends during scrolling. The two most important properties for this are:

`start` and `end`. 

These tell ScrollTrigger where in the scroll journey to start and stop your animation.

## 🔹 What is `start`?

`start` defines when the animation should begin — based on the scroll position.

- **🔢 Numeric Value**
  
  You can set it directly with a number (in pixels):

  ```js
  scrollTrigger: {
    start: 400
  }
  ```
  - This means the animation will start after the page has been scrolled *400px* from the top
- **🧭 Positional Keywords**
  
  You can also define start using keywords to make the behavior more responsive and intuitive.
  ```js 
  start: "triggerPosition viewportPosition"
  ```
  - *triggerPosition* → refers to a point on the trigger element

  - *viewportPosition* → refers to a point on the viewport (screen)

  **📌 Keyword options:**

  | Position | Meaning                                     |
  | -------- | ------------------------------------------- |
  | `top`    | The **top edge** of the element/viewport    |
  | `center` | The **center** of the element/viewport      |
  | `bottom` | The **bottom edge** of the element/viewport |


  **📌 Example: "top center"**
  ```js
  scrollTrigger: {
    trigger: ".square",
    start: "top center"
  } 
  ```
  This means:

  - Start the animation when the `top` of .square reaches the `center` of the viewport.

  So if you're scrolling down the page:

    - The trigger element will slide into view

    - When its `top` touches the `center` of the screen → the animation begins
  
  **🎯 You Can Mix Percentages and Pixels**

  ```js 
  start: "top 30%"
  // or
  start: "center 200px"
  ``` 
  - `"top 30%"` → Start when the `top` of the trigger reaches `30%` down the viewport

  - `"center 200px"` → Start when the `center` of the trigger reaches `200px` down from the top  of the viewport

- **⚡ Dynamic `start` and `end` using offsetHeight**
  
  Example:

  ```js
  end: () => `+=${document.querySelector(".square").offsetHeight}`
  ```

  This means:

  - The animation will run for a distance equal to the height of the `.square` element.

  - The `+=` tells ScrollTrigger to go that many pixels after the start point.

  🧠 In simpler terms:

  - “Start the animation when .square hits the center of the screen, and run it for the height of that element.”

  This is very helpful if your element’s height might change or be dynamic — it ensures your scroll animation duration matches the actual element size.
### 🧪 Default Behavior
If you don’t define `start` and `end`, the default is:

```js 
start: "top bottom"
end: "bottom top"
```
This means:

  - Animation starts when the `top of the trigger` hits the `bottom of the viewport`

  - Animation ends when the `bottom of the trigger` hits the `top of the viewport`

### 🎛️ ScrollTrigger `toggleClass`
The `toggleClass` property in ScrollTrigger allows you to automatically add or remove a CSS class to an element based on the scroll position — without writing separate event listeners.

This is useful for:

  - Triggering a visual state change (like changing color or visibility)

  - Activating animations defined in CSS

  - Toggling UI elements when an element enters or exits the viewport

#### 🧪 Example:

```js 
gsap.to(".square", {
  scrollTrigger: {
    trigger: ".square",
    start: "top center",
    toggleClass: "red"
  }
});
```

This will:

  - Add the `red` class to `.square` when the element scrolls into view (based on the `start` value)

  - Remove the class when it scrolls out again

#### 🧙‍♂️ How it works:
| Scroll State        | What Happens               |
| ------------------- | -------------------------- |
| Element enters view | `red` class is **added**   |
| Element leaves view | `red` class is **removed** |

### ✅ Visualizing with Markers
To see exactly where the `start` and `end` points are, enable `markers`:
```js
scrollTrigger: {
  trigger: ".square",
  start: "top center",
  end: "bottom top",
  markers: true
}
```
This will add little indicators to the screen showing where the scroll trigger begins and ends — very useful for debugging and learning!

### 🎨 Customize the Marker Appearance
You can style these markers using the markers object:

```js
markers: {
  startColor: "blue",
  endColor: "yellow",
  fontSize: "12px",
  indent: 20
}
```
| Property     | Description                                                                      |
| ------------ | -------------------------------------------------------------------------------- |
| `startColor` | Changes the color of the **start marker line** (default is green)                |
| `endColor`   | Changes the color of the **end marker line** (default is red)                    |
| `fontSize`   | Sets the font size of the marker labels (like "start", "end")                    |
| `indent`     | Adds horizontal space between the markers and the edge of the screen (in pixels) |


 This control allows you to make animations respond naturally to scroll position — making your web pages feel more dynamic and interactive ✨