# Understanding Forms and Tables

## a. Table structure

Tables are used to display data in rows and columns.

```html
<table>
  <tr>
    <th>Name</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Adhul</td>
    <td>18</td>
  </tr>
  <tr>
    <td>Rema</td>
    <td>45</td>
  </tr>
</table>
```

**`<table>`** — the container for the entire table

**`<tr>`** (table row) — defines a single row

**`<th>`** (table header) — defines a header cell, usually bold and centered by default, used for column titles

**`<td>`** (table data) — defines a regular data cell

**Structure logic:** `<table>` contains multiple `<tr>` (rows), and each `<tr>` contains multiple `<td>` or `<th>` (cells).

## b. Form elements

A `<form>` is a container that collects user input and usually sends it somewhere (like a server) when submitted.

**Input** — the most common form element, used for various types of user input (text, email, password, etc.)

```html
<input type="text" name="username">
```

**Textarea** — for multi-line text input (like a message or comment box)

```html
<textarea rows="4" cols="30"></textarea>
```

**Select** — a dropdown menu, using `<option>` for each choice

```html
<select>
  <option value="html">HTML</option>
  <option value="css">CSS</option>
  <option value="js">JavaScript</option>
</select>
```

**Button** — a clickable button, often used to submit a form

```html
<button type="submit">Submit</button>
```

## c. Input types

The `type` attribute on `<input>` changes both its behavior and appearance.

**Text** — a basic single-line text field

```html
<input type="text" placeholder="Enter your name">
```

**Email** — expects an email format, browser shows a basic validation error if the format is wrong (e.g., missing `@`)

```html
<input type="email" placeholder="Enter your email">
```

**Password** — masks the input (shows dots/asterisks instead of actual characters)

```html
<input type="password">
```

**Radio** — lets the user pick **only one** option from a group (grouped using the same `name`)

```html
<input type="radio" name="gender" value="male"> Male
<input type="radio" name="gender" value="female"> Female
```

**Checkbox** — lets the user select **multiple** independent options

```html
<input type="checkbox" name="hobby" value="reading"> Reading
<input type="checkbox" name="hobby" value="coding"> Coding
```

**File** — lets the user upload a file from their device

```html
<input type="file">
```

## d. Basic form validation attributes

These attributes help validate user input directly in the browser, before any data is even sent anywhere.

**`required`** — the field must be filled in before the form can be submitted

```html
<input type="text" required>
```

**`placeholder`** — shows light gray hint text inside the field, disappears once the user starts typing (not an actual value, just a hint)

```html
<input type="text" placeholder="Enter your name">
```

**`pattern`** — defines a specific format the input must match, using a regular expression (regex)

```html
<input type="text" pattern="[A-Za-z]{3,}" title="At least 3 letters, no numbers">
```

This example forces the input to be at least 3 letters long, with no numbers/symbols allowed.

**Why this matters:** these attributes provide basic **client-side validation** — catching obvious mistakes immediately in the browser, before the data is even sent to a server. This improves user experience (instant feedback) but isn't a substitute for proper server-side validation, since browser validation can be bypassed.