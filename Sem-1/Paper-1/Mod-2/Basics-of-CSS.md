# Understanding the Basics of CSS

## a. What is CSS, and how does it work with HTML

**CSS (Cascading Style Sheets)** is a language used to style and visually design HTML content — things like colors, fonts, spacing, layout, and positioning.

**How it works with HTML:** HTML provides the **structure/content** of a page (headings, paragraphs, images, etc.), while CSS controls **how that content looks** (colors, size, spacing, layout). They work together — HTML without CSS is just plain, unstyled text and elements stacked top to bottom; CSS is what makes a page actually look designed.

**Simple analogy:** HTML is like the skeleton/structure of a house (walls, rooms, doors), and CSS is the paint, furniture, and interior design — same structure can look completely different depending on the styling applied.

## b. Ways to apply CSS

**Inline CSS** — written directly inside an HTML element's `style` attribute, applies only to that one element

```html
<p style="color: blue;">This text is blue.</p>
```

**Internal CSS** — written inside a `<style>` tag, placed in the `<head>` of the HTML document, applies to the whole page

```html
<head>
  <style>
    p {
      color: blue;
    }
  </style>
</head>
```

**External CSS** — written in a completely separate `.css` file, linked to the HTML document using a `<link>` tag

```html
<head>
  <link rel="stylesheet" href="style.css">
</head>
```
```css
/* style.css */
p {
  color: blue;
}
```

**Which is best?** External CSS is the most commonly used and recommended approach — it keeps HTML (structure) and CSS (styling) separate, makes styles reusable across multiple pages, and is easier to maintain as a project grows.

## c. CSS syntax (selectors, properties, values)

A CSS rule follows this basic structure:

```css
selector {
  property: value;
}
```

**Example:**
```css
p {
  color: blue;
  font-size: 16px;
}
```

**Selector** — targets which HTML element(s) the styling should apply to (in this example, `p` — all paragraph tags)

**Property** — the specific style aspect being changed (`color`, `font-size`, `margin`, etc.)

**Value** — the actual setting applied to that property (`blue`, `16px`, etc.)

**Reading it in plain English:** "For all `<p>` elements, set the text color to blue and the font size to 16 pixels."

## d. Types of selectors

**Element selector** — targets all elements of a specific tag type

```css
p {
  color: red;
}
```
(Applies to every `<p>` on the page)

**Class selector** — targets elements with a specific `class` attribute, written with a `.` before the name. Can be reused on multiple elements.

```html
<p class="highlight">This is highlighted</p>
```
```css
.highlight {
  background-color: yellow;
}
```

**ID selector** — targets a single, unique element with a specific `id` attribute, written with a `#` before the name. Should only be used once per page (unlike class).

```html
<p id="main-title">Welcome</p>
```
```css
#main-title {
  font-size: 24px;
}
```

**Group selector** — applies the same styles to multiple different selectors at once, separated by commas

```css
h1, h2, p {
  font-family: Arial, sans-serif;
}
```
(Applies the same font to all `h1`, `h2`, and `p` elements, avoiding repeating the same rule multiple times)

**Key difference between class and id:** a **class** can be applied to many elements (reusable styling), while an **id** should be unique to just one element on the page (used for specific, one-off targeting, often also used with JavaScript to select that exact element).