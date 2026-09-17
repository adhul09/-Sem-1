# DOM & Browser Programming

## a. DOM Structure and Element Selection

**DOM** = Document Object Model. It's how JavaScript "sees" your HTML page — as a tree of elements you can access and change.

```html
<body>
  <h1 id="title">Hello</h1>
  <p class="text">Some text</p>
</body>
```

**Selecting elements:**
```js
document.getElementById("title");        // selects by id
document.querySelector(".text");         // selects first match (CSS-style selector)
document.querySelectorAll("p");          // selects ALL matching elements
```

`querySelector` and `querySelectorAll` are the most commonly used today — they work like CSS selectors (`.class`, `#id`, `tag`).

---

## b. DOM Manipulation for Real-World Interactions

Once you've selected an element, you can change it:

```js
const title = document.querySelector("#title");

title.textContent = "New Heading";     // change text
title.style.color = "blue";            // change CSS style
title.classList.add("highlight");      // add a CSS class
title.classList.remove("highlight");   // remove a CSS class
```

**Creating and adding new elements:**
```js
const newPara = document.createElement("p");
newPara.textContent = "I'm a new paragraph!";
document.body.appendChild(newPara);
```

---

## c. Event Handling and User Interaction

Events let you respond to what the user does (click, type, hover, etc.)

```js
const button = document.querySelector("#myButton");

button.addEventListener("click", () => {
  console.log("Button was clicked!");
});
```

**Common events:** `click`, `input`, `submit`, `mouseover`, `keydown`

```js
const input = document.querySelector("#nameInput");
input.addEventListener("input", (e) => {
  console.log("User typed:", e.target.value);
});
```

---

## d. Browser Object Model (BOM) Basics

BOM = everything the browser gives you access to *outside* the actual webpage content — window size, URL, history, etc.

```js
window.innerWidth;         // browser window width
window.location.href;      // current page URL
window.location.reload();  // reload the page
window.history.back();     // go to previous page
alert("Hello!");           // popup alert box
```

Note: `window` is the global object in browsers — you've actually been using it all along without realizing (e.g., `console` is technically `window.console`).