# Error Handling & Debugging

## a. try, catch, finally, throw

- **try** — code you want to attempt, which might fail
- **catch** — runs if something in `try` goes wrong
- **finally** — always runs, whether it succeeded or failed
- **throw** — manually create your own error

```js
try {
  let result = riskyFunction();
  console.log(result);
} catch (error) {
  console.log("Something went wrong:", error.message);
} finally {
  console.log("This runs no matter what.");
}
```

**Throwing your own error:**
```js
function checkAge(age) {
  if (age < 0) {
    throw new Error("Age cannot be negative");
  }
  return age;
}

try {
  checkAge(-5);
} catch (error) {
  console.log(error.message); // "Age cannot be negative"
}
```

---

## b. Handling Runtime Errors Properly

Runtime errors happen while the code is running (not while writing it) — e.g., calling a function on `undefined`, or dividing by something invalid.

**Good practice:**
- Don't just wrap *everything* in try/catch — only wrap code that could realistically fail (API calls, JSON parsing, user input handling)
- Always give a useful fallback or message, not just an empty catch block
- Example of handling a common real error — parsing JSON that might be invalid:
```js
try {
  const data = JSON.parse(userInput);
} catch (error) {
  console.log("Invalid JSON format provided");
}
```

---

## c. Reading and Understanding Error Messages

Common error types you'll see:

| Error Type         | Meaning                                      | Example cause |
|---------------------|-----------------------------------------------|----------------|
| `ReferenceError`    | Using a variable that doesn't exist            | `console.log(x)` when `x` was never defined |
| `TypeError`         | Using a value in a way its type doesn't allow  | Calling `.map()` on `undefined` |
| `SyntaxError`       | Broken code structure                          | Missing bracket or comma |
| `RangeError`        | Number outside allowed range                   | Invalid array length |

**How to read an error message:**
1. Look at the **error type** first (TypeError, ReferenceError, etc.)
2. Read the **message** — it usually tells you exactly what went wrong
3. Check the **line number** shown — that's where to start looking
4. Work backward from there — often the *real* bug is a line or two above

---

## d. Debugging Logic Using Browser Tools and AI Assistance

**Browser DevTools (Chrome/Edge — press F12):**
- **Console tab** — see errors and use `console.log()` to check values
- **Sources tab** — set **breakpoints** (click a line number) to pause code and inspect variables step by step
- **Network tab** — check if API calls are succeeding/failing

**Simple debugging habit:**
```js
console.log("Value of x before calculation:", x);
```
Sprinkle these around your code to see what's actually happening at each step — this alone solves most beginner bugs.

**Using AI for debugging:**
- Paste the exact error message + the relevant code snippet
- Ask "what does this error mean and why is it happening here?"
- Ask it to explain the fix, not just give the answer — so you actually learn the reasoning