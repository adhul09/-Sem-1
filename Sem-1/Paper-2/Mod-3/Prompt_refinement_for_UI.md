# Prompt Refinement for UI Components

## What is prompt refinement?

Improving a prompt step by step so the AI gives output that is closer to what you actually need. The first answer is rarely perfect, so you adjust the prompt by adding specific details.

## 1. Controlling output

### a. Format

Format means **what form the answer comes in**. Tell the AI exactly what you want back.

**Things you can specify:**
- Language and style: "React functional component using hooks, not a class component"
- Styling approach: "plain CSS in a separate file" or "inline styles" or "Tailwind classes"
- File type: "give me one `.jsx` file" or "give JSX and CSS separately"
- Code only vs explanation: "give only the code, no explanation" or "explain each part briefly"
- Version or tooling: "React with Vite, using React Router v6"

**Vague prompt:**
```
Make a button component.
```

**Refined prompt (with format):**
```
Create a React functional component called PrimaryButton using hooks-free JSX.
Use a separate CSS file for styling. Give the JSX and the CSS in two separate
code blocks, with no extra explanation.
```

### b. Structure

Structure means **how the answer is organized and how the component is designed**.

**Things you can specify:**
- Props the component should accept: "props: label, onClick, disabled"
- Folder and file layout: "put it in `components/`, one component per file"
- Sections or order of the answer: "first the component, then usage example, then CSS"
- Behavior details: "show a hover effect and a disabled state"
- Limits: "keep it under 40 lines, no external libraries"

**Vague prompt:**
```
Make a product card.
```

**Refined prompt (with structure):**
```
Create a React ProductCard component with props: image, title, price and
onAddToCart. Layout: image on top, title below it, price and an "Add to Cart"
button at the bottom. Put it in components/ProductCard.jsx. Then show a usage
example that renders three cards from an array using map. Do not use any
external libraries.
```

## Refining step by step

If the first answer is not right, do not start over. Ask for specific changes:

```
Good, but make the button full width, change the color to blue, and add a
loading state that shows "Adding..." while the request is in progress.
```

**A simple checklist for a good UI prompt:**

| Include | Example |
|---|---|
| What to build | "A responsive navbar" |
| Tools and versions | "React + Vite, plain CSS" |
| Props and behavior | "props: links, logo; collapses on mobile" |
| Output format | "JSX and CSS in separate blocks, code only" |
| Constraints | "no external libraries, under 50 lines" |

## Always check the output

AI can still give wrong or outdated code, such as old React Router syntax. Run the code, read through it, and check anything unfamiliar against the official documentation before using it.
