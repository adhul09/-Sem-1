# Understanding Text, Media, and Linking in HTML

## a. Text formatting tags

**Bold** — `<b>` makes text bold with no extra meaning (purely visual)

```html
<b>This text is bold</b>
```

**Strong** — `<strong>` also makes text bold, but semantically means the content is **important**

```html
<strong>This text is important</strong>
```

**Italic** — `<i>` makes text italic with no extra meaning (purely visual)

```html
<i>This text is italic</i>
```

**Emphasis** — `<em>` also makes text italic, but semantically means the content should be **emphasized** (e.g., changes the tone/stress of a sentence)

```html
<em>This text is emphasized</em>
```

**Underline** — `<u>` underlines text (mostly visual, used carefully since underlines are usually associated with links)

```html
<u>This text is underlined</u>
```

**Key difference:** `<b>`/`<i>`/`<u>` are purely visual styling. `<strong>`/`<em>` carry semantic meaning (importance/emphasis) in addition to visual styling — screen readers announce `<strong>` and `<em>` differently, but treat `<b>`/`<i>` as plain text.

## b. Lists

**Ordered list** — `<ol>`, numbered list, used when order/sequence matters

```html
<ol>
  <li>Wake up</li>
  <li>Brush teeth</li>
  <li>Eat breakfast</li>
</ol>
```

**Unordered list** — `<ul>`, bulleted list, used when order doesn't matter

```html
<ul>
  <li>Apples</li>
  <li>Bananas</li>
  <li>Mangoes</li>
</ul>
```

**Description list** — `<dl>`, used for term-description pairs (like a glossary)

```html
<dl>
  <dt>HTML</dt>
  <dd>A markup language used to structure web pages</dd>

  <dt>CSS</dt>
  <dd>A language used to style web pages</dd>
</dl>
```
(`<dt>` = description term, `<dd>` = description detail)

## c. Image handling and paths

**Relative path** — points to a file **relative to the current file's location**, doesn't include the full address

```html
<img src="images/cat.jpg">
```
This means: "look inside a folder called `images`, in the same location as this HTML file."

**Absolute path** — the full, complete address of a file, either a full URL or the full location on the system

```html
<img src="https://example.com/images/cat.jpg">
```

**Why this matters:**
- Relative paths are preferred for images/files that live within your own project — they keep working even if you move the whole project folder elsewhere (like uploading to GitHub or a server), since the relationship between files stays the same
- Absolute paths are needed when linking to something hosted elsewhere (an external image, another website)

## d. Hyperlinks and navigation between pages

The `<a>` (anchor) tag creates clickable links, using the `href` attribute to specify the destination.

**Linking to an external website:**

```html
<a href="https://google.com">Go to Google</a>
```

**Linking to another page within your own project:**

```html
<a href="about.html">About Us</a>
```

**Opening a link in a new tab:**

```html
<a href="https://google.com" target="_blank">Go to Google</a>
```

**Linking to a section within the same page** (using an `id`):

```html
<a href="#contact">Jump to Contact section</a>
...
<h2 id="contact">Contact</h2>
```

This is how multi-page websites are connected — each page is its own `.html` file, and `<a>` tags with relative paths link them together into a navigable site.