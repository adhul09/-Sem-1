# Understand NPM and Package Management

## 1. Initializing a Node.js Project

**npm** (Node Package Manager) comes bundled with Node.js. To start a new project:

```bash
npm init
```
This asks a series of questions (project name, version, entry point, etc.) and creates a `package.json` file.

**Faster way (skip the questions, use defaults):**
```bash
npm init -y
```

**What `package.json` looks like:**
```json
{
  "name": "my-app",
  "version": "1.0.0",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {}
}
```
This file is the **identity card** of your project — it tracks the project's name, version, scripts, and all installed packages.

---

## 2. Installing and Managing Packages

**Install a package:**
```bash
npm install express
```
or the shorter form:
```bash
npm i express
```

**Install a package only needed for development (not production):**
```bash
npm install --save-dev nodemon
```

**Uninstall a package:**
```bash
npm uninstall express
```

**Install everything listed in package.json (e.g., after cloning a project):**
```bash
npm install
```

When you install a package, it:
- Gets added to the `dependencies` (or `devDependencies`) section in `package.json`
- Gets downloaded into a `node_modules` folder
- Gets locked to a specific version in `package-lock.json`

---

## 3. Understanding Dependency Management

**Dependencies** = other people's code (packages) your project relies on to work.

```json
"dependencies": {
  "express": "^4.18.2",
  "mongoose": "^7.0.3"
}
```

**Version number meaning (`^4.18.2`):**
- `4` = major version (big changes, may break things)
- `18` = minor version (new features, safe updates)
- `2` = patch version (bug fixes only)
- `^` = allows automatic updates to minor/patch versions, but not major

**`node_modules` folder:**
- Contains the actual code of every installed package
- Very large — should **never** be pushed to GitHub
- Always add it to `.gitignore`

**`.gitignore` example:**
```
node_modules/
.env
```

**Why this matters:** Anyone who clones your project just needs `package.json` — they run `npm install` to download the exact same dependencies themselves, instead of you having to upload the entire `node_modules` folder.
