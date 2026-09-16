# Thinking with AI

Using AI well is a skill in itself — it's not just about asking questions, but asking them in a way that actually helps you learn and solve problems.

## a. Using AI For

### i. Code Explanation
Instead of just copying code, ask AI to explain **why** it works, line by line if needed.

**Good prompt:**
```
Explain what this code does line by line, and why the reduce() 
function is used here instead of a for loop.
```

### ii. Debugging
Give AI the exact error message + the relevant code — not the whole project, just the part that's failing.

**Good prompt:**
```
I'm getting this error: "TypeError: Cannot read property 'map' 
of undefined" on this line: [paste code]. What's causing it and 
how do I fix it?
```

---

## b. Prompt Types

### i. Instruction-based prompts
You directly tell the AI exactly what to do.
```
Write a function that removes duplicate values from an array.
```

### ii. Context-based prompts
You give background/context first, so the AI tailors its answer to your specific situation.
```
I'm a beginner learning the MERN stack. I understand basic loops 
but not array methods yet. Explain map() in a simple way with an 
example a beginner would understand.
```
Context-based prompts usually give much more useful, relevant answers than plain instructions alone — because the AI adjusts its explanation to your actual level and situation.

---

## c. Asking Step-by-Step Explanations

When something is confusing, explicitly ask for a step-by-step breakdown rather than a single-paragraph answer.

**Example prompt:**
```
Explain async/await step by step, starting from why it exists, 
what problem it solves, and then show a simple example.
```

**Why this matters:** A single dense explanation is easy to forget. A step-by-step breakdown mirrors how you'd actually learn a new concept — building one idea on top of the previous one, which sticks better, especially under time pressure like exam prep.

**General tip for using AI while learning (not just for exams):**
Always try to understand *why* something works before moving to the next topic — pasting code without understanding it will catch up to you later when you need to write similar logic yourself without help.