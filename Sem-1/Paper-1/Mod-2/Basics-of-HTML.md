# Understanding the Basics of HTML

## a. Structure of an HTML document

Every HTML document follows a basic skeleton structure.

Eg:

```html
<!DOCTYPE html>
<html>
<head>
  <title>My Page</title>
</head>
<body>
  <h1>Hello World</h1>
</body>
</html>
```

**`<!DOCTYPE html>`**
- Tells the browser which version of HTML is being used (HTML5)
- Must be the first line — not an actual HTML tag, more of an instruction to the browser

**`<html>`**
- The root element — wraps everything else on the page

**`<head>`**
- Contains metadata — information about the page that isn't directly displayed (title, linked CSS, character encoding, etc.)

**`<body>`**
- Contains everything visible on the page — text, images, buttons, links

## b. Common HTML elements

**Headings** — `<h1>` to `<h6>`, used for titles/section headers

```html
<h1>Main Title</h1>
<h2>Subheading</h2>
```

**Paragraphs** — `<p>`, used for blocks of text

```html
<p>This is a paragraph of text.</p>
```

**Links** — `<a>`, creates clickable links

```html
<a href="https://google.com">Go to Google</a>
```

**Images** — `<img>`, displays an image (self-closing tag)

```html
<img src="cat.jpg" alt="A cute cat">
```

## c. Attributes and their usage

Attributes provide extra information about an element, written as `name="value"` pairs inside the opening tag.

**`href`** (used with `<a>`) — specifies the URL the link points to

```html
<a href="https://github.com">GitHub</a>
```

**`src`** (used with `<img>`) — specifies the source file/path

```html
<img src="photo.png">
```

**`alt`** (used with `<img>`) — alternate text shown if the image fails to load, also used by screen readers

```html
<img src="photo.png" alt="A sunset over mountains">
```

**`title`** — shows a tooltip when hovering over an element

```html
<a href="https://github.com" title="Visit GitHub">GitHub</a>
```

## d. Semantic vs non-semantic tags

**Semantic tags** — clearly describe their meaning/purpose

```html
<header>...</header>
<nav>...</nav>
<article>...</article>
<footer>...</footer>
```

**Non-semantic tags** — generic containers with no inherent meaning, used for grouping/styling

```html
<div>...</div>
<span>...</span>
```

Semantic tags improve accessibility (screen readers can navigate more meaningfully), help SEO (search engines understand page structure better), and make code more readable for other developers.

**Rule of thumb:** use semantic tags when a clear standard meaning exists; use `<div>`/`<span>` only when no semantic tag fits.