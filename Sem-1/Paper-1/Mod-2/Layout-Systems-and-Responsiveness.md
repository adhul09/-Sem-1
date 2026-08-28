# Understanding Layout Systems and Responsiveness

## a. Flexbox fundamentals (container, items, alignment)

Flexbox is a layout system for arranging elements in a single row or column, with easy control over alignment and spacing.

**Container** — the parent element, given `display: flex`

```css
.container {
  display: flex;
}
```

**Items** — the direct children of the flex container, automatically arranged in a row by default

```html
<div class="container">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>
```

**Alignment properties:**

```css
.container {
  display: flex;
  justify-content: center;   /* aligns items horizontally */
  align-items: center;       /* aligns items vertically */
}
```

- `justify-content` — controls alignment along the main axis (horizontal, by default)
- `align-items` — controls alignment along the cross axis (vertical, by default)

## b. Grid basics (rows, columns, gap)

CSS Grid is a layout system for arranging elements in a two-dimensional grid (rows AND columns at once).

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: auto auto;
  gap: 10px;
}
```

- `grid-template-columns` — defines how many columns and their widths (`1fr` means "one fraction of available space")
- `grid-template-rows` — defines how many rows and their heights
- `gap` — sets spacing between grid items (both rows and columns)

**Simple difference from Flexbox:** Flexbox is best for one-dimensional layouts (a single row or column), Grid is best for two-dimensional layouts (rows and columns together, like a full page layout).

## c. Responsive design concepts

**Responsive design** means building web pages that automatically adjust and look good across different screen sizes — phones, tablets, laptops, desktops.

Key concepts:
- **Fluid layouts** — using relative units (`%`, `fr`, `vw`/`vh`) instead of fixed pixel widths, so elements resize with the screen
- **Flexible images** — images that scale with their container instead of staying a fixed size

```css
img {
  max-width: 100%;
  height: auto;
}
```

- **Mobile-first approach** — designing for small screens first, then adding styles for larger screens as needed

## d. Media queries for different screen sizes

**Media queries** let you apply different CSS rules based on the screen size (or other device characteristics).

```css
/* Default styles for mobile */
body {
  font-size: 14px;
}

/* Styles applied only when screen width is 768px or more */
@media (min-width: 768px) {
  body {
    font-size: 18px;
  }
}
```

This example keeps text smaller on mobile screens by default, and increases the font size once the screen is at least 768px wide (typical tablet/desktop breakpoint). Media queries are the core mechanism that makes responsive design actually work.