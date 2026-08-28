# Understanding Styling and Layout with CSS

## a. Colors, fonts, and text styling

**Colors** can be set using different formats — named colors, HEX, RGB.

```css
p {
  color: red;              /* named color */
  color: #ff0000;          /* HEX */
  color: rgb(255, 0, 0);   /* RGB */
}
```

**Fonts** control the typeface, size, and weight of text.

```css
p {
  font-family: Arial, sans-serif;
  font-size: 16px;
  font-weight: bold;
}
```

**Text styling** — additional properties to control text appearance.

```css
p {
  text-align: center;
  text-decoration: underline;
  text-transform: uppercase;
}
```

## b. Box model (margin, border, padding, content)

Every HTML element is treated as a rectangular box made up of four layers, from inside out:

```
+-----------------------------------+
|             margin                |
|  +-----------------------------+  |
|  |          border             |  |
|  |  +-----------------------+  |  |
|  |  |       padding         |  |  |
|  |  |  +-----------------+  |  |  |
|  |  |  |     content     |  |  |  |
|  |  |  +-----------------+  |  |  |
|  |  +-----------------------+  |  |
|  +-----------------------------+  |
+-----------------------------------+
```

- **Content** — the actual text/image inside the element
- **Padding** — space between the content and the border (inside the box)
- **Border** — the line around the padding
- **Margin** — space outside the border, between this element and others

```css
div {
  padding: 10px;
  border: 2px solid black;
  margin: 20px;
}
```

## c. Display properties (block, inline, inline-block, none)

**`block`** — takes up the full width available, starts on a new line (e.g., `<div>`, `<p>`, `<h1>`)

```css
div {
  display: block;
}
```

**`inline`** — takes up only as much width as needed, does not start on a new line (e.g., `<span>`, `<a>`). Cannot set width/height on it.

```css
span {
  display: inline;
}
```

**`inline-block`** — behaves like `inline` (doesn't force a new line) but allows setting width/height like `block`

```css
span {
  display: inline-block;
  width: 100px;
  height: 50px;
}
```

**`none`** — completely hides the element, removes it from the page layout entirely (not just invisible — takes up no space)

```css
div {
  display: none;
}
```

## d. Positioning (static, relative, absolute, fixed, sticky)

**`static`** — default positioning, follows normal document flow, `top`/`left`/etc. have no effect

**`relative`** — positioned relative to its own normal position, can be shifted using `top`/`left`/`right`/`bottom` without affecting other elements

```css
div {
  position: relative;
  top: 10px;
  left: 20px;
}
```

**`absolute`** — removed from normal flow, positioned relative to the nearest **positioned** ancestor (an ancestor with `relative`/`absolute`/`fixed`), or the whole page if none exists

```css
div {
  position: absolute;
  top: 0;
  right: 0;
}
```

**`fixed`** — positioned relative to the browser window, stays in place even when scrolling

```css
div {
  position: fixed;
  bottom: 0;
  right: 0;
}
```

**`sticky`** — behaves like `relative` until the page is scrolled past a certain point, then acts like `fixed`

```css
div {
  position: sticky;
  top: 0;
}
```