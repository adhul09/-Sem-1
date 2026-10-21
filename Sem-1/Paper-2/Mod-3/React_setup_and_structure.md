# Understanding React Setup and Project Structure

## 1. Setting up a React project using Vite

**Vite** is a fast build tool used to create and run modern React projects.

```bash
npm create vite@latest my-app -- --template react
cd my-app
npm install
npm run dev
```

The dev server usually starts at `http://localhost:5173`.
Web applications utilize different rendering paradigms to deliver HTML and JavaScript to the user's browser, with profound consequences for initial load time, TTFB (Time to First Byte), and SEO.
## 2. Project structure and file organization

Project structure means how the files and folders of a React application are organized. A good structure makes the project easier to understand, maintain, and scale.

```
my-app/
  node_modules/      -> installed packages (never push to GitHub)
  public/            -> static files served as-is (favicon, images)
  src/               -> all your React code lives here
    assets/          -> images, icons
    App.jsx          -> main/root component
    App.css          -> styles for App
    main.jsx         -> entry point of the React app
    index.css        -> global styles
  index.html         -> the single HTML page
  package.json       -> project info, scripts, dependencies
  vite.config.js     -> Vite configuration
  .gitignore
```

**Key idea:** you write almost everything inside `src/`.

## 3. Role of vite.config.js (basic idea)

It is the configuration file for Vite. In a basic project it just registers the React plugin, which lets Vite understand JSX.

```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
})
```

Later it can be used for things like changing the dev server port or setting up a proxy to your backend.

## 4. How the app runs and builds

**How it runs:**
- `index.html` contains one empty `<div id="root"></div>` and loads `src/main.jsx`
- `main.jsx` tells React to render the `<App />` component inside that div

```jsx
import { createRoot } from 'react-dom/client'
import App from './App.jsx'

createRoot(document.getElementById('root')).render(<App />)
```

**Scripts in package.json:**

| Command | What it does |
|---|---|
| `npm run dev` | Starts the development server (updates instantly when you save) |
| `npm run build` | Creates an optimized production build in the `dist/` folder |
| `npm run preview` | Previews the production build locally |
